project('http', 'c', version: '1.0.0')

src = files('./src/http.c')

include_dir = include_directories('./include')

http = library(
    'http',
    src,
    include_directories: [include_dir],
    install: not meson.is_subproject(),
)
http_dep = declare_dependency(
    include_directories: include_dir,
    link_with: http,
)

pkg_mod = import('pkgconfig')

pkg_mod.generate(
    http,
    name: 'http',
    description: 'Simple http client',
    libraries: http,
    version: meson.project_version(),
)

if get_variable('tests')
    subdir('./test')
endif