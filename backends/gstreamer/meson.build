gstreamer_backend_sources = [
  'rb-encoder-gst.h',
  'rb-encoder-gst.c',
  'rb-player-gst-helper.c',
  'rb-player-gst-helper.h',
  'rb-player-gst.h',
  'rb-player-gst.c',
  'rb-player-gst-xfade.h',
  'rb-player-gst-xfade.c',
]

gstreamer_backend_c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="Rhythmbox"',
]

librbbackendsgstreamer = static_library('rbbackendsgstreamer',
  gstreamer_backend_sources,
  c_args: gstreamer_backend_c_args,
  dependencies: [gdk_pixbuf, gstreamer, gtk, libxml],
  include_directories: [
    configinc, libinc, metadatainc, backendsinc, rhythmdbinc,
  ],
  install: 'true',
  link_args: ['-export-dynamic'],
)
