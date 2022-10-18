sles_spec1 = vcs_tag(
    input : '../cxl-tool.spec.in',
    output : 'cxl-tool.spec.sles.in',
    command: vcs_tagger,
    replace_string : 'VERSION',
)

header = files('header')

sles_spec2 = custom_target('cxl-tool.spec.in',
  command : [
    'cat', header, '@INPUT@',
  ],
  input : sles_spec1,
  output : 'cxl-tool.spec.in',
  capture : true,
)

sles_spec3 = custom_target('cxl-tool.spec',
  command : [
    'sed', '-e', 's,CXL_DNAME,libcxl-devel,g',
           '-e', 's,%license,%doc,g',
           '-e', 's,\(^License:.*GPL\)v2,\1-2.0,g',
           '-e', 's,CXL_LNAME,libcxl@0@,g'.format(LIBCXL_CURRENT - LIBCXL_AGE),
	   '@INPUT@'
  ],

  input : sles_spec2,
  output : 'cxl-tool.spec',
  capture : true,
)
