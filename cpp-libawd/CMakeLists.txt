cmake_minimum_required (VERSION 2.6)

project ( libawd )

add_definitions(-D_7ZIP_ST)


# does this system provide the strncpy_s functions?

include (${CMAKE_ROOT}/Modules/CheckFunctionExists.cmake)
check_function_exists ( strncpy_s HAVE_STRNCPY_S )
check_function_exists ( strlcpy HAVE_STRLCPY )



set( ZLIB_SOURCES
      lib/zlib/adler32.c
      lib/zlib/crc32.c
      lib/zlib/crc32.h
      lib/zlib/deflate.c
      lib/zlib/deflate.h
      lib/zlib/inffast.c
      lib/zlib/inffast.h
      lib/zlib/inffixed.h
      lib/zlib/inflate.c
      lib/zlib/inflate.h
      lib/zlib/inftrees.c
      lib/zlib/inftrees.h
      lib/zlib/trees.c
      lib/zlib/trees.h
      lib/zlib/zconf.h
      lib/zlib/zlib.h
      lib/zlib/zutil.c
      lib/zlib/zutil.h
    )


set( LZMA_SOURCES
      lib/lzma/Alloc.c
      lib/lzma/Alloc.h
      lib/lzma/Bra.c
      lib/lzma/Bra.h
      lib/lzma/LzFind.c
      lib/lzma/LzFind.h
      lib/lzma/LzHash.h
      lib/lzma/LzmaDec.c
      lib/lzma/LzmaDec.h
      lib/lzma/LzmaEnc.c
      lib/lzma/LzmaEnc.h
      lib/lzma/LzmaLib.c
      lib/lzma/LzmaLib.h
      lib/lzma/Types.h
    )


set( LIB_CC_INCLUDES
      include/anim.h
      include/attr.h
      include/awd_types.h
      include/awd.h
      include/awdlzma.h
      include/awdzlib.h
      include/block.h
      include/camera.h
      include/geomutil.h
      include/geomutilhelper.h
      include/hgversion.h
      include/libawd.h
      include/light.h
      include/material.h
      include/mesh.h
      include/message.h
      include/meta.h
      include/method.h
      include/name.h
      include/ns.h
      include/platform.h
      include/primitive.h
      include/scene.h
      include/shading.h
      include/shadows.h
      include/skelanim.h
      include/skeleton.h
      include/stream.h
      include/texture.h
      include/util.h
      include/uvanim.h
      include/vertexanim.h
    )


set( LIB_CC_SOURCES
      src/anim.cc
      src/attr.cc
      src/awd.cc
      src/awdlzma.cc
      src/awdzlib.cc
      src/block.cc
      src/camera.cc
      src/geomutil.cc
      src/geomutilhelper.cc
      src/light.cc
      src/material.cc
      src/mesh.cc
      src/message.cc
      src/meta.cc
      src/method.cc
      src/name.cc
      src/ns.cc
      src/primitive.cc
      src/scene.cc
      src/shading.cc
      src/shadows.cc
      src/skelanim.cc
      src/skeleton.cc
      src/stream.cc
      src/texture.cc
      src/util.cc
      src/uvanim.cc
      src/vertexanim.cc
      ${LIB_CC_INCLUDES}
      ${LZMA_SOURCES}
      ${ZLIB_SOURCES}
    )


# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories( "${PROJECT_SOURCE_DIR}/include" )
include_directories( "${PROJECT_SOURCE_DIR}/lib/zlib" )
include_directories( "${PROJECT_SOURCE_DIR}/lib/lzma" )

# build a static library
#
add_library( awd_static STATIC ${LIB_CC_SOURCES} )

# build a shared library
#
add_library( awd SHARED ${LIB_CC_SOURCES} )




# add the install targets
install (TARGETS awd DESTINATION lib)
install (TARGETS awd_static DESTINATION lib)

# install includes
install (FILES ${LIB_CC_INCLUDES}
         DESTINATION include/awd)