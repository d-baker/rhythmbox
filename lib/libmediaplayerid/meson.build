mpid_headers = [
  'mediaplayerid.h'
]

install_headers(mpid_headers, subdir: 'rhythmbox/lib/libmediaplayerid')

mpid_sources = [
  'mpid-private.h',
  'mpid-device.c',
  'mpid-files.c',
  'mpid-util.c'
]

mpid_deps = [gio, gio_unix, glib, gobject]

# use the GUdev/media-player-id implementation if possible,
# otherwise HAL.
if use_gudev
  mpid_sources += ['mpid-udev.c']
  mpid_deps += [gudev]
elif use_hal
  mpid_sources += ['mpid-hal.c']
  mpid_deps += [dbus_glib, hal]
else
  mpid_sources += ['mpid-dummy.c']
endif

libmpid = static_library('mediaplayerid', mpid_sources,
  install: 'true',
  dependencies: mpid_deps,
)
