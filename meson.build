project(
    'delaunator-cpp',
    'cpp',
    version : '3.0.1',
    license : 'MIT',
    default_options : [
        'cpp_std=c++20',
    ],
    meson_version:'>=1.1',
)

del_inc = include_directories('include')

if get_option('header_only')
    delaunator_dep = declare_dependency(
        include_directories : del_inc,
        compile_args : '-DDELAUNATOR_HEADER_ONLY',
    )
else
    del_lib = static_library(
        'delaunator',
        'include/delaunator.cpp',
        include_directories : del_inc,
    )

    delaunator_dep = declare_dependency(
        link_with: del_lib,
        include_directories : del_inc,
    )
endif

if not meson.is_subproject()
    example_inc = include_directories('examples')

    executable(
        'basic',
        'examples/basic.cpp',
        dependencies : delaunator_dep,
        include_directories : example_inc,
    )
endif