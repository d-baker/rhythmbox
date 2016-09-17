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
  dependencies: [podcast_dep],
  include_directories: [shellinc, sourcesinc, widgetsinc],
  install: 'true',
  link_args: ['-export-dynamic'],
)

source_sync_dep = declare_dependency(
  link_with: libsourcesync,
  include_directories: include_directories('.')
)
