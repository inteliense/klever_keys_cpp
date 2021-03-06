cmake_minimum_required(VERSION 3.21)
project(klever_keys)

set(CMAKE_CXX_STANDARD 14)

##TODO fill in the paths below
#custom variables
set(CUSTOM_LIBRARY_PATH /opt/homebrew/opt) # /path/to/libraries/dir
set(OPENSSL_PATH /usr/local/) # /path/to/library/dir
set(BOOST_PATH /opt/homebrew/opt/boost@1.76) # /path/to/library/dir
set(INSTALL_PARENT_DIR /usr/local) # /path/to/install/dir

set(OPENSSL_LIBRARY_PATH ${OPENSSL_PATH}/lib)
set(OPENSSL_HEADERS_PATH ${OPENSSL_PATH}/include)
set(BOOST_LIBRARY_PATH ${BOOST_PATH}/lib)
set(BOOST_HEADERS_PATH ${BOOST_PATH}/include)
set(INSTALL_PATH_LIB ${INSTALL_PARENT_DIR}/lib)
set(INSTALL_PATH_HEADERS ${INSTALL_PARENT_DIR}/include)

set(CMAKE_LIBRARY_PATH ${CMAKE_LIBRARY_PATH} ${CUSTOM_LIBRARY_PATH})
link_directories(${OPENSSL_LIBRARY_PATH} ${BOOST_LIBRARY_PATH})
include_directories(${OPENSSL_HEADERS_PATH} ${BOOST_HEADERS_PATH})

find_library(OpenSSL openssl
        PATHS ${OPENSSL_PATH})
find_library(Crypto crypto
        PATHS ${OPENSSL_PATH})
find_library(Boost boost
        PATHS ${BOOST_PATH})

#static library
add_library(klever_keys HideString.h KleverKeys.h KleverKeys.cpp
        easy_encrypt/EasyEncrypt.cpp easy_encrypt/EasyEncrypt.h
        easy_encrypt/Base64.h)

#shared library
#add_library(klever_keys SHARED HideString.h KleverKeys.h KleverKeys.cpp)

target_link_libraries(${PROJECT_NAME} ssl crypto)
set_target_properties(klever_keys PROPERTIES PREFIX "")

#static library install
install(TARGETS ${PROJECT_NAME} DESTINATION ${INSTALL_DIR})

#shared libary install (TODO)
#install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION ${INSTALL_DIR}
#        PUBLIC_HEADER DESTINATION ${INSTALL_PATH_HEADERS})
