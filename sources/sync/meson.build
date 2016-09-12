sourcesync_sources = [
  'rb-sync-settings.c',
  'rb-sync-settings.h',
  'rb-sync-settings-ui.c',
  'rb-sync-settings-ui.h',
  'rb-sync-state.c',
  'rb-sync-state.h',
  'rb-sync-state-ui.c',
  'rb-sync-state-ui.h'
]

sourcesync_c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="Rhythmbox"',
  '-DPIXMAP_DIR="' + get_option('datadir') + '/pixmaps"',
  '-DSHARE_DIR="' + get_option('datadir') + '"',
  '-DDATADIR="' + get_option('datadir') + '"',
]

if use_no_strict_aliasing
  sourcesync_c_args += ['-fno-strict-aliasing']
endif

libsourcesync = static_library('sourcesync', sourcesync_sources,
  c_args: sourcesync_c_args,
  include_directories: [
    configinc, backendsinc, libinc, libmediaplayeridinc, metadatainc,
    podcastinc, rhythmdbinc, shellinc, sourcesinc, widgetsinc,
  ],
  dependencies: [ gio, glib, gobject, gstreamer_pbutils, gtk, libxml ],
  install: 'true',
  link_args: ['-export-dynamic'],
)
