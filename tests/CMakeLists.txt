python_tests_init()

add_python_style_test(python_static_analysis "${PROJECT_SOURCE_DIR}/gaia")
add_python_style_test(python_test_static_analysis "${PROJECT_SOURCE_DIR}/tests")


add_docstring_test(gaia.core.base)
add_docstring_test(gaia.core.task)
add_docstring_test(gaia.core.port)
add_docstring_test(gaia.esgf.search)
add_docstring_test(gaia.pandas.geopandas_writer)

add_python_test(version)
add_python_test(factory)
add_python_test(gaiaObject)
add_python_test(message)
add_python_test(stream)
add_python_test(port)
add_python_test(task)
add_python_test(geopandas)
add_python_test(esgf_search)
