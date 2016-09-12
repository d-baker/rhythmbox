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

rb_c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="Rhythmbox"',
]


librbwidgets = static_library('rbwidgets', widget_sources,
  c_args: rb_c_args,
  include_directories: [
    configinc, backendsinc, libinc, metadatainc, rhythmdbinc, shellinc,
    sourcesinc
  ],
  dependencies: [
    gstreamer, gstreamer_pbutils, gtk, libnotify, libsoup, libxml
  ],
  install: 'true',
  link_args: ['-export-dynamic'],
  link_with: [librb, librhythmdb]
)

# These are interactive UI tests.

test_rb_segmented_bar = executable('test-rb-segmented-bar', 'test-rb-segmented-bar.c',
  dependencies: [gtk],
  link_with: librbwidgets)

test_uri_dialog = executable('test-uri-dialog', 'test-uri-dialog.c',
  dependencies: [gtk],
  include_directories: [libinc],
  link_with: [librb, librbwidgets])
