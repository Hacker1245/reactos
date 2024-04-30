
add_definitions(-D__WINESRC__)
include_directories(${REACTOS_SOURCE_DIR}/sdk/include/reactos/wine)
spec2def(adsldp.dll adsldp.spec)

list(APPEND SOURCE
    adsldp.c
    ldap.c
    precomp.h)

add_library(adsldp MODULE
    ${SOURCE}
    ${CMAKE_CURRENT_BINARY_DIR}/adsldp.def)

add_typelib(adsldp.idl)
set_module_type(adsldp win32dll)
target_link_libraries(adsldp wine)
add_importlibs(adsldp ole32 oleaut32 secur32 activeds uuid)
add_pch(adsldp precomp.h SOURCE)
add_cd_file(TARGET adsldp DESTINATION reactos/system32 FOR all)
