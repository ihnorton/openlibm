list(APPEND SRCS
    invtrig.c k_cosl.c k_sinl.c
    k_tanl.c s_exp2l.c
)

if(NOT ${WIN32})
    list(APPEND SRCS s_nanl.c)
endif()

foreach(SRCFILE ${SRCS})
    list(APPEND REL_SRCS "${CMAKE_CURRENT_SOURCE_DIR}/${SRCFILE}")
endforeach()

set(SRCS "${REL_SRCS}" PARENT_SCOPE)
