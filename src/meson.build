pkgdatadir = join_paths(get_option('prefix'), get_option('datadir'), meson.project_name())
moduledir = join_paths(pkgdatadir, 'courier')
gnome = import('gnome')

gnome.compile_resources('courier',
  'courier.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', join_paths(get_option('prefix'), get_option('localedir')))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'courier.in',
  output: 'courier',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir')
)

courier_sources = [
  '__init__.py',
  'main.py',
  'window.py',
  'request_panel.py',
  'constants.py',
  'sidebar.py',
  'request_handler.py',
  'collection_manager.py',
  'tab_panel.py'
]

install_data(courier_sources, install_dir: moduledir)
