project('libassert', 'cpp')

cpptrace = subproject('cpptrace')
cpptrace_dep = cpptrace.get_variable('cpptrace_dep')
cpptrace_lib = cpptrace.get_variable('cpptrace_lib')

flags = ['-DLIBASSERT_SAFE_COMPARISONS']

libassert = library(
    'libassert',
    'src/analysis.cpp',
    'src/assert.cpp',
    'src/paths.cpp',
    'src/platform.cpp',
    'src/printing.cpp',
    'src/stringification.cpp',
    'src/tokenizer.cpp',
    'src/utils.cpp',
    include_directories : 'include',
    build_by_default : true,
    install : true,
    pic : true,
    dependencies : [cpptrace_dep],
    cpp_args : flags,
    build_rpath : '$ORIGIN',
    install_rpath : '$ORIGIN',
)

install_subdir(
    'include',
    strip_directory : true,
    install_dir : get_option('includedir'),
)

pkg = import('pkgconfig')
pkg.generate(libassert, extra_cflags : flags)

libassert_dep = declare_dependency(
    include_directories : 'include',
    link_with : libassert,
    dependencies : [cpptrace_dep],
    compile_args : flags,
)
