desktop_in_files = [ 'rhythmbox.desktop.in', 'rhythmbox-device.desktop.in' ]
foreach desktop_in_file : desktop_in_files
  configure_file(
    input: desktop_in_file + '.in',
    output: desktop_in_file,
    configuration: cdata
  )
endforeach

# This is done with intltool in the Makefile.am, but there's no need to
# use intltool any more.
playlists_xml = custom_target('playlists.xml',
  input: 'playlists.xml.in',
  output: 'playlists.xml',
  command: ['msgfmt', '--xml', '-d', '../po', '--template', '@INPUT@', '-o', '@OUTPUT@'],
)
