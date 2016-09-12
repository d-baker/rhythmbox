headers = [
  'rb-refstring.h',
  'rhythmdb.h',
  'rhythmdb-property-model.h',
  'rhythmdb-query-model.h',
  'rhythmdb-query-result-list.h',
  'rhythmdb-query-results.h',
  'rhythmdb-import-job.h',
  'rhythmdb-entry.h',
  'rhythmdb-entry-type.h',
  'rhythmdb-metadata-cache.h'
]

install_headers(headers, subdir: 'rhythmbox/rhythmdb')

sources = [
  'rb-refstring.c',
  'rhythmdb-private.h',
  'rhythmdb.c',
  'rhythmdb-monitor.c',
  'rhythmdb-query.c',
  'rhythmdb-property-model.c',
  'rhythmdb-query-model.c',
  'rhythmdb-query-result-list.c',
  'rhythmdb-query-results.c',
  'rhythmdb-import-job.c',
  'rhythmdb-entry-type.c',
  'rhythmdb-song-entry-types.c',
  'rhythmdb-dbus.c',
  'rhythmdb-metadata-cache.c'
]

if get_option('database') == 'tree'
  sources += ['rhythmdb-tree.h', 'rhythmdb-tree.c']
endif

c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="RhythmDB"',
  '-DSHARE_DIR="' + get_option('datadir') + '"',
  '-DDATADIR="' + get_option('datadir') + '"'
]

if use_no_strict_aliasing
  c_args += ['-fno-strict-aliasing']
endif

librhythmdb = static_library('rhythmdb', sources,
  # GStreamer and Gtk are included in some lib/ headers, so we have to depend
  # on them here to use librb. In case you wonder why a database library
  # requires a GUI or audio playback...
  c_args: c_args,
  dependencies: [gio, glib, gobject, gstreamer, gtk, libmath, libxml, tdb],
  include_directories: [configinc, libinc, metadatainc, podcastinc, widgetsinc],
  link_args: '-export-dynamic',
  link_with: [librb, librbmetadata])
