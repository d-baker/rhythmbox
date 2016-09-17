subdir('sync')

source_headers = [
  'rb-source.h',
  'rb-streaming-source.h',
  'rb-source-search.h',
  'rb-display-page.h',
  'rb-display-page-group.h',
  'rb-display-page-tree.h',
  'rb-display-page-menu.h',
  'rb-display-page-model.h',
  'rb-browser-source.h',
  'rb-media-player-source.h',
  'rb-playlist-source.h',
  'rb-playlist-xml.h',
  'rb-auto-playlist-source.h',
  'rb-static-playlist-source.h',
  'rb-source-search-basic.h',
  'rb-device-source.h',
  'rb-transfer-target.h'
]

install_headers(source_headers, subdir: 'rhythmbox/sources')

source_sources = [
  'rb-source.c',
  'rb-streaming-source.c',
  'rb-source-search.c',
  'rb-display-page.c',
  'rb-display-page-group.c',
  'rb-display-page-tree.c',
  'rb-display-page-menu.c',
  'rb-display-page-model.c',
  'rb-browser-source.c',
  'rb-library-source.c',
  'rb-library-source.h',
  'rb-media-player-source.c',
  'rb-playlist-source.c',
  'rb-auto-playlist-source.c',
  'rb-static-playlist-source.c',
  'rb-play-queue-source.c',
  'rb-play-queue-source.h',
  'rb-missing-files-source.c',
  'rb-missing-files-source.h',
  'rb-import-errors-source.c',
  'rb-import-errors-source.h',
  'rb-source-search-basic.c',
  'rb-device-source.c',
  'rb-transfer-target.c'
]

source_c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="Rhythmbox"',
  '-DPIXMAP_DIR="' + get_option('datadir') + '/pixmaps"',
  '-DSHARE_DIR="' + get_option('datadir') + '"',
  '-DDATADIR="' + get_option('datadir') + '"',
]

if use_no_strict_aliasing
  source_c_args += ['-fno-strict-aliasing']
endif

sources_dependencies = [backends_dep, source_sync_dep, totem_plparser]

libsources = static_library('sources', source_sources,
  c_args: source_c_args,
  include_directories: [ shellinc, widgetsinc, ],
  dependencies: sources_dependencies,
  install: 'true',
  link_args: ['-export-dynamic'],
)

sources_dep = declare_dependency(
  link_with: libsources
)
