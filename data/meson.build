desktop_in_files = [ 'rhythmbox.desktop.in', 'rhythmbox-device.desktop.in' ]
foreach desktop_in_file : desktop_in_files
  configure_file(
    input: desktop_in_file + '.in',
    output: desktop_in_file,
    configuration: cdata
  )
endforeach
