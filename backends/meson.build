subdir('gstreamer')

backend_headers = [
  'rb-encoder.h',
  'rb-player.h',
  'rb-player-gst-filter.h',
  'rb-player-gst-tee.h'
]

install_headers(backend_headers, subdir: 'rhythmbox/backends')

backend_sources = [
  'rb-encoder.c',
  'rb-player.c',
  'rb-player-gst-filter.c',
  'rb-player-gst-tee.c',
]

backend_c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="Rhythmbox"',
]

backend_dependencies = [gstreamer_backend_dep]

librbbackends = static_library('rbbackends', backend_sources,
  c_args: backend_c_args,
  dependencies: backend_dependencies,
  install: 'true',
  link_args: ['-export-dynamic'],
)

backends_dep = declare_dependency(
  link_with: librbbackends,
  dependencies: gstreamer_backend_dep,
  include_directories: include_directories('.')
)
