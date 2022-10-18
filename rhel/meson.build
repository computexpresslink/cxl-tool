rhel_spec1 = vcs_tag(
    input : '../cxl-tool.spec.in',
    output : 'cxl-tool.spec.in',
    command: vcs_tagger,
    replace_string : 'VERSION',
)

rhel_spec2 = custom_target('ndctl.spec',
  command : [
    'sed', '-e', 's,CXL_DNAME,cxl-devel,g',
	   '-e', '/^%defattr.*/d',
	   '-e', 's,CXL_LNAME,cxl-libs,g',
	   '@INPUT@'
  ],
  input : rhel_spec1,
  output : 'cxl-tool.spec',
  capture : true,
)
