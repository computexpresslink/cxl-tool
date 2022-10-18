bashcompletiondir = get_option('bashcompletiondir')
if bashcompletiondir == ''
  bash_completion = dependency('bash-completion', required : false)
  if bash_completion.found()
      bashcompletiondir = bash_completion.get_pkgconfig_variable('completionsdir')
  else
    bashcompletiondir = datadir / 'bash-completion/completions'
  endif
endif

if bashcompletiondir != 'no'
  install_data('cxl-tool', install_dir : bashcompletiondir)

# TODO Switch to symlinks once 0.61.0 is more widely available
#  install_symlink('cxl',
#    install_dir : bashcompletiondir,
#    pointing_to : 'cxl-tool'
#  )
  install_data('cxl-tool', rename : 'cxl', install_dir : bashcompletiondir)
endif

modprobedatadir = get_option('modprobedatadir')
if modprobedatadir == ''
  modprobedatadir = sysconfdir + '/modprobe.d/'
endif
