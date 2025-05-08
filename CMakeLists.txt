cmake_minimum_required(VERSION 3.3...4.0)
project(FCG2025-1)

# Define o padrão do C++
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Configura o FetchContent
include(FetchContent)

# Configura o GLFW
FetchContent_Declare(
        glfw
        GIT_REPOSITORY https://github.com/glfw/glfw.git
        GIT_TAG 3.4  # Versão mais estável
)
FetchContent_MakeAvailable(glfw)

# Configura o GLM
FetchContent_Declare(
        glm
        GIT_REPOSITORY https://github.com/g-truc/glm.git
        GIT_TAG 1.0.1
)
FetchContent_MakeAvailable(glm)

# Configura a STB
FetchContent_Declare(
        stb
        GIT_REPOSITORY https://github.com/nothings/stb.git
        GIT_TAG master
)
FetchContent_MakeAvailable(stb)

add_compile_options(-Wno-pragmas)

# Configuração do GLAD
set(GLAD_DIR "${CMAKE_SOURCE_DIR}/common/glad.c")
set(GLAD_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include/glad/glad.h")

# Add novas pastas se necessário
set(SYSTEMS_DIR
        "${CMAKE_SOURCE_DIR}/common/systems/game.cpp"
        "${CMAKE_SOURCE_DIR}/common/systems/resourceManager.cpp"
)

set(ENTITIES_DIR
        "${CMAKE_SOURCE_DIR}/common/entities"
)

set(UTILITY_DIR
        "${CMAKE_SOURCE_DIR}/common/utility/shader.cpp"
        "${CMAKE_SOURCE_DIR}/common/utility/texture2D.cpp"
)

# Verifica se os arquivos do GLAD existem
if(NOT EXISTS ${GLAD_DIR} OR NOT EXISTS ${GLAD_INCLUDE_DIR})
    message(FATAL_ERROR "Arquivos do GLAD não encontrados!\n"
            "Por favor, baixe a GLAD manualmente em https://glad.dav1d.de/\n"
            "Configuração necessária:\n"
            "- API: OpenGL\n"
            "- Profile: Core\n"
            "- Version: 4.1 (ou superior)\n"
            "- Gerar um loader\n"
            "Coloque glad.h em include/glad/ e glad.c em common/")
endif()

# Configura includes
include_directories(
        ${CMAKE_SOURCE_DIR}/include
        ${CMAKE_SOURCE_DIR}/include/systems
        ${CMAKE_SOURCE_DIR}/include/entities
        ${CMAKE_SOURCE_DIR}/include/utility
        ${CMAKE_SOURCE_DIR}/include/glad
        ${CMAKE_SOURCE_DIR}/common
        ${glm_SOURCE_DIR}
        ${stb_SOURCE_DIR}
)

# Configuração de bibliotecas por sistema operacional
if(WIN32)
    set(OPENGL_LIBS opengl32)
elseif(APPLE)
    find_library(OPENGL_LIBS OpenGL)
else()
    find_package(OpenGL REQUIRED)
    set(OPENGL_LIBS OpenGL::GL)
endif()

# Arquivos
set(SRC
        main
)

# Para cada exercício
foreach(SRC ${SRC})
    get_filename_component(EXE_NAME ${SRC} NAME)

    # Caminho do arquivo fonte
    set(SOURCE_FILE "src/${SRC}.cpp")

    # Verifica se o arquivo fonte existe
    if(NOT EXISTS ${CMAKE_SOURCE_DIR}/${SOURCE_FILE})
        message(WARNING "Arquivo fonte ${SOURCE_FILE} não encontrado, pulando...")
        continue()
    endif()

    # Cria o executável
    add_executable(${EXE_NAME} ${SOURCE_FILE} ${GLAD_DIR} ${SYSTEMS_DIR} ${ENTITIES_DIR} ${UTILITY_DIR})

    # Configura includes e bibliotecas
    target_include_directories(${EXE_NAME} PRIVATE
            ${CMAKE_SOURCE_DIR}/include/glad
            ${glm_SOURCE_DIR}
            ${stb_SOURCE_DIR}
    )

    target_link_libraries(${EXE_NAME} PRIVATE
            glfw
            ${OPENGL_LIBS}
            glm::glm
    )

    # No Windows, precisa vincular com kernel32 e user32
    if(WIN32)
        target_link_libraries(${EXE_NAME} PRIVATE kernel32 user32)
    endif()
endforeach()

# Mensagem de sucesso
message(STATUS "Configuração do projeto concluída com sucesso!")