set(BOX64_ROOT "${CMAKE_CURRENT_SOURCE_DIR}/..")
find_program(CCACHE_FOUND ccache)
if(CCACHE_FOUND)
    set_property(GLOBAL PROPERTY RULE_LAUNCH_COMPILE ccache)
    set_property(GLOBAL PROPERTY RULE_LAUNCH_LINK ccache)
else()
    message(SEND_ERROR "ccache not found!")
endif()

set(INTERPRETER
    "${BOX64_ROOT}/src/emu/x64run.c"
    "${BOX64_ROOT}/src/emu/x64run0f.c"
    "${BOX64_ROOT}/src/emu/x64run64.c"
    "${BOX64_ROOT}/src/emu/x64run66.c"
    "${BOX64_ROOT}/src/emu/x64run660f.c"
    "${BOX64_ROOT}/src/emu/x64run66f20f.c"
    "${BOX64_ROOT}/src/emu/x64run66f30f.c"
    "${BOX64_ROOT}/src/emu/x64run6664.c"
    "${BOX64_ROOT}/src/emu/x64run66d9.c"
    "${BOX64_ROOT}/src/emu/x64run66dd.c"
    "${BOX64_ROOT}/src/emu/x64run66f0.c"
    "${BOX64_ROOT}/src/emu/x64run67.c"
    "${BOX64_ROOT}/src/emu/x64run67avx.c"
    "${BOX64_ROOT}/src/emu/x64run67_32.c"
    "${BOX64_ROOT}/src/emu/x64run6764_32.c"
    "${BOX64_ROOT}/src/emu/x64run670f.c"
    "${BOX64_ROOT}/src/emu/x64run6766.c"
    "${BOX64_ROOT}/src/emu/x64run67660f.c"
    "${BOX64_ROOT}/src/emu/x64rund8.c"
    "${BOX64_ROOT}/src/emu/x64rund9.c"
    "${BOX64_ROOT}/src/emu/x64runda.c"
    "${BOX64_ROOT}/src/emu/x64rundb.c"
    "${BOX64_ROOT}/src/emu/x64rundc.c"
    "${BOX64_ROOT}/src/emu/x64rundd.c"
    "${BOX64_ROOT}/src/emu/x64runde.c"
    "${BOX64_ROOT}/src/emu/x64rundf.c"
    "${BOX64_ROOT}/src/emu/x64runf0.c"
    "${BOX64_ROOT}/src/emu/x64runf20f.c"
    "${BOX64_ROOT}/src/emu/x64runf30f.c"
    "${BOX64_ROOT}/src/emu/x64runavx.c"
    "${BOX64_ROOT}/src/emu/x64runavx0f.c"
    "${BOX64_ROOT}/src/emu/x64runavx0f38.c"
    "${BOX64_ROOT}/src/emu/x64runavx660f.c"
    "${BOX64_ROOT}/src/emu/x64runavxf20f.c"
    "${BOX64_ROOT}/src/emu/x64runavxf30f.c"
    "${BOX64_ROOT}/src/emu/x64runavx660f38.c"
    "${BOX64_ROOT}/src/emu/x64runavx660f3a.c"
    "${BOX64_ROOT}/src/emu/x64runavxf20f38.c"
    "${BOX64_ROOT}/src/emu/x64runavxf30f38.c"
    "${BOX64_ROOT}/src/emu/x64runavxf20f3a.c"
    "${BOX64_ROOT}/src/emu/x64runavxf30f3a.c"
)

set(DYNAREC_SRC
"${BOX64_ROOT}/src/dynarec/dynablock.c"
"${BOX64_ROOT}/src/dynarec/dynarec_native.c"
"${BOX64_ROOT}/src/dynarec/dynarec_native_functions.c"
"${BOX64_ROOT}/src/emu/x64test.c"
)

set(DYNAREC_SRC
${DYNAREC_SRC}

"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_functions.c"
"${BOX64_ROOT}/src/dynarec/arm64/arm64_immenc.c"
"${BOX64_ROOT}/src/dynarec/arm64/arm64_printer.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_jmpnext.c"

"${BOX64_ROOT}/src/dynarec/arm64/arm64_prolog.S"
"${BOX64_ROOT}/src/dynarec/arm64/arm64_epilog.S"
"${BOX64_ROOT}/src/dynarec/arm64/arm64_next.S"
"${BOX64_ROOT}/src/dynarec/arm64/arm64_lock.S"
)

set(DYNAREC_PASS
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_helper.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_emit_tests.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_emit_math.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_emit_logic.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_emit_shift.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_00.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_0f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_64.c"
#"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_65.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_66.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_67.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_67_32.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_67_avx.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_6764_32.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_d8.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_d9.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_da.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_db.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_dc.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_dd.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_de.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_df.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_f0.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_660f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_66f20f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_66f30f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_6664.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_66f0.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_f20f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_f30f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_0f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_0f38.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_66_0f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_f2_0f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_f3_0f.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_66_0f38.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_66_0f3a.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_f2_0f38.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_f2_0f3a.c"
"${BOX64_ROOT}/src/dynarec/arm64/dynarec_arm64_avx_f3_0f38.c"
)

set(DYNAREC_PASS
# "${BOX64_ROOT}/src/wrapped/generated/wrapper.h"
${DYNAREC_PASS}
"${BOX64_ROOT}/src/dynarec/dynarec_native_pass.c"
)
include_directories(
    "${BOX64_ROOT}/src/include"
    "${BOX64_ROOT}/src"
)
add_definitions(-DDYNAREC)
add_definitions(-DARM64)
add_definitions(-Disnanf=isnan)
add_definitions(-Disinff=__inline_isinff)
add_definitions(-Dsincos=__sincos)
enable_language(ASM)

add_library(dynarec_native OBJECT ${DYNAREC_SRC})

add_library(native_pass0 OBJECT ${DYNAREC_PASS})
set_target_properties(native_pass0 PROPERTIES COMPILE_FLAGS "-DSTEP=0")
add_library(native_pass1 OBJECT ${DYNAREC_PASS})
set_target_properties(native_pass1 PROPERTIES COMPILE_FLAGS "-DSTEP=1")
add_library(native_pass2 OBJECT ${DYNAREC_PASS})
set_target_properties(native_pass2 PROPERTIES COMPILE_FLAGS "-DSTEP=2")
add_library(native_pass3 OBJECT ${DYNAREC_PASS})
set_target_properties(native_pass3 PROPERTIES COMPILE_FLAGS "-DSTEP=3")
add_library(test_interpreter OBJECT ${INTERPRETER})
set_target_properties(test_interpreter PROPERTIES COMPILE_FLAGS "-DTEST_INTERPRETER")

add_library(dynarec STATIC
$<TARGET_OBJECTS:dynarec_native>
$<TARGET_OBJECTS:native_pass0>
$<TARGET_OBJECTS:native_pass1>
$<TARGET_OBJECTS:native_pass2>
$<TARGET_OBJECTS:native_pass3>
$<TARGET_OBJECTS:test_interpreter>
)

add_library(interpreter OBJECT ${INTERPRETER})

add_library(box64-core STATIC 
    "${BOX64_ROOT}/src/dynarec/dynarec.c"

    "${BOX64_ROOT}/src/emu/x64compstrings.c"
    "${BOX64_ROOT}/src/emu/x64emu.c"
    "${BOX64_ROOT}/src/emu/x64int3.c"
    "${BOX64_ROOT}/src/emu/x87emu_private.c"
    "${BOX64_ROOT}/src/emu/x64primop.c"
    "${BOX64_ROOT}/src/emu/x64run_private.c"
    "${BOX64_ROOT}/src/emu/x64shaext.c"
    # "${BOX64_ROOT}/src/emu/x64syscall.c"
    # "${BOX64_ROOT}/src/emu/x64tls.c"
    "${BOX64_ROOT}/src/emu/x64trace.c"
    "${BOX64_ROOT}/src/custommem.c"
    "${BOX64_ROOT}/src/box64context.c"
    "${BOX64_ROOT}/src/libtools/threads.c"
    "${BOX64_ROOT}/src/tools/rbtree.c"
    "${BOX64_ROOT}/src/tools/bridge.c"
    "${BOX64_ROOT}/src/tools/pathcoll.c"
    "${BOX64_ROOT}/src/tools/my_cpuid.c"
    "${BOX64_ROOT}/src/librarian/dictionnary.c"
)


target_link_libraries(box64-core dynarec)
target_link_libraries(box64-core interpreter)

target_include_directories(box64-core PUBLIC
    "${BOX64_ROOT}/src/include"
)

target_compile_definitions(box64-core PRIVATE
STATICBUILD=1
)