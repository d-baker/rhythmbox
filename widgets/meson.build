widget_headers = [
  'rb-alert-dialog.h',
  'rb-entry-view.h',
  'rb-property-view.h',
  'rb-dialog.h',
  'rb-cell-renderer-pixbuf.h',
  'rb-cell-renderer-rating.h',
  'rb-rating.h',
  'rb-library-browser.h',
  'rb-segmented-bar.h',
  'rb-song-info.h',
  'rb-source-toolbar.h',
  'rb-uri-dialog.h',
  'rb-fading-image.h',
  'rb-object-property-editor.h',
  'rb-import-dialog.h',
  'rb-button-bar.h',
  'rb-task-list-display.h',
  'rb-encoding-settings.h'
]

install_headers(widget_headers, subdir: 'rhythmbox/widgets')

widget_sources = [
  'rb-alert-dialog.c',
  'rb-entry-view.c',
  'rb-property-view.c',
  'rb-search-entry.c',
  'rb-search-entry.h',
  'rb-header.c',
  'rb-header.h',
  'rb-dialog.c',
  'rb-cell-renderer-pixbuf.c',
  'rb-cell-renderer-rating.c',
  'gossip-cell-renderer-expander.c',
  'gossip-cell-renderer-expander.h',
  'rb-song-info.c',
  'rb-rating.c',
  'rb-rating-helper.c',
  'rb-segmented-bar.c',
  'rb-library-browser.c',
  'rb-rating-helper.h',
  'rb-query-creator.c',
  'rb-query-creator.h',
  'rb-query-creator-private.h',
  'rb-query-creator-properties.c',
  'rb-uri-dialog.c',
  'eggwrapbox.c',
  'eggwrapbox.h',
  'eggwrapbox-enums.c',
  'eggwrapbox-enums.h',
  'rb-source-toolbar.c',
  'rb-fading-image.c',
  'rb-object-property-editor.c',
  'rb-import-dialog.c',
  'rb-button-bar.c',
  'rb-task-list-display.c',
  'rb-encoding-settings.c'
]

widget_c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="Rhythmbox"',
]

widget_dependencies = [ lib_dep, rhythmdb_dep, podcast_dep, libnotify ]

librbwidgets = static_library('rbwidgets', widget_sources,
  c_args: widget_c_args,
  include_directories: [
    backendsinc, shellinc, sourcesinc
  ],
  dependencies: widget_dependencies,
  install: 'true',
  link_args: ['-export-dynamic'],
)

widgets_dep = declare_dependency(
  # We list librhythmdb in both 'link_with' and 'dependencies' due to
  # circular dependency between rhythmdb/ and widgets/.
  link_with: [librhythmdb, librbwidgets],
  dependencies: widget_dependencies,
  include_directories: widgetsinc
)


# These are interactive UI tests.

test_rb_segmented_bar = executable('test-rb-segmented-bar', 'test-rb-segmented-bar.c',
  dependencies: [widgets_dep])

test_uri_dialog = executable('test-uri-dialog', 'test-uri-dialog.c',
  dependencies: [widgets_dep])
