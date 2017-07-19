configure_file( setup.py.tpl setup.py )

install( DIRECTORY pyflann DESTINATION share/flann/python )
install( FILES ${CMAKE_CURRENT_BINARY_DIR}/setup.py DESTINATION share/flann/python )


# python instalation
if (PYTHON_EXECUTABLE)
    # COMMAND sudo ${PYTHON_EXECUTABLE} ${CMAKE_CURRENT_BINARY_DIR}/setup.py install
    install(CODE "execute_process(
        COMMAND sudo -H pip install ${CMAKE_CURRENT_BINARY_DIR}
        WORKING_DIRECTORY \"${CMAKE_CURRENT_SOURCE_DIR}\")")
endif()
