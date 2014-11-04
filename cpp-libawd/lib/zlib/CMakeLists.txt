
set( SOURCE_FILES
      adler32.c
      crc32.c
      crc32.h
      deflate.c
      deflate.h
      inffast.c
      inffast.h
      inffixed.h
      inflate.c
      inflate.h
      inftrees.c
      inftrees.h
      trees.c
      trees.h
      zconf.h
      zlib.h
      zutil.c
      zutil.h
    )

add_library( zlib STATIC ${SOURCE_FILES} )