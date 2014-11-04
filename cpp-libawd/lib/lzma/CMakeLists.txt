
set( SOURCE_FILES
      Alloc.c
      Alloc.h
      Bra.c
      Bra.h
      LzFind.c
      LzFind.h
      LzHash.h
      LzmaDec.c
      LzmaDec.h
      LzmaEnc.c
      LzmaEnc.h
      LzmaLib.c
      LzmaLib.h
      Types.h
    )

add_library( lzma STATIC ${SOURCE_FILES} )