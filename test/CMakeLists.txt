# test opendialog
add_executable(test_opendialog test_opendialog.c)

set_target_properties(test_opendialog PROPERTIES
	CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)
target_link_libraries(test_opendialog PRIVATE nativefiledialog)

# test opendialogmultiple
add_executable(test_opendialogmultiple test_opendialogmultiple.c)

set_target_properties(test_opendialogmultiple PROPERTIES
	CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)
target_link_libraries(test_opendialogmultiple PRIVATE nativefiledialog)

# test pickfolder
add_executable(test_pickfolder test_pickfolder.c)

set_target_properties(test_pickfolder PROPERTIES
	CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)
target_link_libraries(test_pickfolder PRIVATE nativefiledialog)

# test savedialog
add_executable(test_savedialog test_savedialog.c)

set_target_properties(test_savedialog PROPERTIES
	CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)
target_link_libraries(test_savedialog PRIVATE nativefiledialog)

