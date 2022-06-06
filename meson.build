project('bx', 'cpp')

# credit: https://github.com/JohnathanFL/bx-meson/blob/master/meson.build

inc_bx = include_directories('include')
inc_3rd = include_directories('3rdparty')

cpp = meson.get_compiler('cpp')
pthread = cpp.find_library('pthread')
dl = cpp.find_library('dl', required: true)
gl = dependency('GL')

cpp_args = []

if get_option('buildtype') == 'release'
  cpp_args += '-DBX_CONFIG_DEBUG=0'
else
  cpp_args += '-DBX_CONFIG_DEBUG=1'
endif

bx = library('bx',
             files('src/amalgamated.cpp'),
             cpp_args: cpp_args,
             include_directories: [
               inc_bx,
               inc_3rd,
             ],
             dependencies: [
               dl,
               gl,
               pthread
             ])

bx_dep = declare_dependency(
  link_with: bx,
  include_directories: [
    inc_bx,
    inc_3rd
  ],
  compile_args: cpp_args
)
