check = dependency('check', required: false)

if check.found()
  executable('test-rhythmdb', ['test-rhythmdb.c', 'test-utils.c'],
      dependencies: [widgets_dep, check])
endif
