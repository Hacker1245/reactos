
add_definitions(-D__WINESRC__)
include_directories(${REACTOS_SOURCE_DIR}/sdk/include/reactos/wine)
spec2def(adsldpc.dll adsldpc.spec)

list(APPEND SOURCE
    main.c)

add_library(adsldpc MODULE
    ${SOURCE}
    ${CMAKE_CURRENT_BINARY_DIR}/adsldpc.def)

set_module_type(adsldpc win32dll)
target_link_libraries(adsldpc wine)
add_importlibs(adsldpc msvcrt kernel32 ntdll)
add_cd_file(TARGET adsldpc DESTINATION reactos/system32 FOR all)
