list(APPEND SRCFILES b_exp.c b_log.c b_tgamma.c)

foreach(SRCFILE ${SRCFILES})
    list(APPEND ${REL_SRCS} "${CMAKE_CURRENT_SOURCE_DIR}/${SRCFILE}")
endforeach()

set(SRCS "${REL_SRCS}" PARENT_SCOPE)
