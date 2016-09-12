podcast_headers = [
  'rb-podcast-entry-types.h',
  'rb-podcast-parse.h',
  'rb-podcast-manager.h',
  'rb-podcast-search.h'
]

install_headers(podcast_headers, subdir: 'rhythmbox/podcast')

podcast_parse_sources = [
  'rb-podcast-parse.c',
  'rb-podcast-parse.h',
  'rb-podcast-search.c',
  'rb-podcast-search-itunes.c',
  'rb-podcast-search-miroguide.c'
]

podcast_sources = [
  'rb-feed-podcast-properties-dialog.c',
  'rb-feed-podcast-properties-dialog.h',
  'rb-podcast-add-dialog.c',
  'rb-podcast-add-dialog.h',
  'rb-podcast-properties-dialog.c',
  'rb-podcast-properties-dialog.h',
  'rb-podcast-main-source.c',
  'rb-podcast-main-source.h',
  'rb-podcast-search.c',
  'rb-podcast-search-itunes.c',
  'rb-podcast-search-miroguide.c',
  'rb-podcast-settings.h',
  'rb-podcast-source.c',
  'rb-podcast-source.h',
  'rb-podcast-parse.c',
  'rb-podcast-manager.c',
  'rb-podcast-entry-types.c'
]

c_args = [
  '-DGNOMELOCALEDIR="' + get_option('datadir') + '/locale"',
  '-DG_LOG_DOMAIN="RhythmBox"'
]

librbpodcast = static_library('rbpodcast', podcast_sources,
  c_args: c_args,
  include_directories: [
    configinc, libinc, metadatainc, podcastinc, rhythmdbinc, shellinc,
    sourcesinc, widgetsinc
  ],
  dependencies: [
    glib, gobject, gstreamer, gtk, json_glib, libsoup, libxml, totem_plparser
  ],
  link_with: librhythmdb)

librbpodcast_parse = static_library('rbpodcast_parse', podcast_parse_sources,
  c_args: c_args,
  include_directories: [configinc, libinc],
  dependencies: [glib, json_glib, libsoup, totem_plparser],
  link_with: librb)

test_podcast_search = executable('test-podcast-search',
  'test-podcast-search.c',
  c_args: c_args,
  include_directories: [configinc, libinc],
  dependencies: [glib, json_glib, totem_plparser],
  link_with: [librbpodcast_parse, librb])

test_podcast_parse = executable('test-podcast-parse',
  'test-podcast-parse.c',
  c_args: c_args,
  include_directories: [configinc, libinc],
  dependencies: [glib, totem_plparser],
  link_with: [librb, librbpodcast_parse])

#
#PLUGIN_FILES = rhythmbox-itms-plugin.c npapi.h npupp.h npruntime.h
#
#if ENABLE_BROWSER_PLUGIN
#plugindir = $(MOZILLA_PLUGINDIR)
#plugin_LTLIBRARIES = librhythmbox-itms-detection-plugin.la
#librhythmbox_itms_detection_plugin_la_SOURCES = $(PLUGIN_FILES)
#librhythmbox_itms_detection_plugin_la_CFLAGS = -I$(top_srcdir)/podcast
#
#librhythmbox_itms_detection_plugin_la_LDFLAGS = \
#	-avoid-version	\
#	-export-symbols $(srcdir)/plugin.symbols \
#	-module
#
#endif
#
#EXTRA_DIST = $(PLUGIN_FILES) plugin.symbols
#
