testcore = [
  'core.c',
  '../util/log.c',
  '../util/sysfs.c',
]

namespace_core = [
  '../util/json.c',
]

cxl_topo = find_program('cxl-topology.sh')
cxl_sysfs = find_program('cxl-region-sysfs.sh')
cxl_labels = find_program('cxl-labels.sh')
cxl_create_region = find_program('cxl-create-region.sh')

tests = [
  [ 'cxl-topology.sh',	      cxl_topo,		  'cxl'   ],
  [ 'cxl-region-sysfs.sh',    cxl_sysfs,	  'cxl'   ],
  [ 'cxl-labels.sh',          cxl_labels,	  'cxl'   ],
  [ 'cxl-create-region.sh',   cxl_create_region,  'cxl'   ],
]

foreach t : tests
  test(t[0], t[1],
    is_parallel : false,
    depends : [
      cxl_tool,
    ],
    suite: t[2],
    timeout : 600,
    env : [
      'TEST_PATH=@0@'.format(meson.current_build_dir()),
      'DATA_PATH=@0@'.format(meson.current_source_dir()),
    ],
  )
endforeach
