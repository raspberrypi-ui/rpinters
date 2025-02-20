sources = files(
  'cc-printers-panel.c',
  'pp-cups.c',
  'pp-details-dialog.c',
  'pp-host.c',
  'pp-ipp-option-widget.c',
  'pp-job.c',
  'pp-jobs-dialog.c',
  'pp-maintenance-command.c',
  'pp-new-printer-dialog.c',
  'pp-new-printer.c',
  'pp-options-dialog.c',
  'pp-ppd-option-widget.c',
  'pp-ppd-selection-dialog.c',
  'pp-print-device.c',
  'pp-printer-entry.c',
  'pp-printer.c',
  'pp-samba.c',
  'pp-utils.c',
  'cc-util.c'
)

ppsources = files (
    'piprint.c'
)

sources += ppsources

resource_data = files(
  'authentication-dialog.ui',
  'new-printer-dialog.ui',
  'ppd-selection-dialog.ui',
  'pp-details-dialog.ui',
  'pp-jobs-dialog.ui',
  'pp-options-dialog.ui',
  'printer-entry.ui',
  'printers.ui'
)

gnome = import('gnome')

cappletname = 'printers'

sources += gnome.compile_resources(
  'cc-' + cappletname + '-resources',
  cappletname + '.gresource.xml',
  c_name: 'cc_' + cappletname,
  dependencies: resource_data,
  export: true
)

add_global_arguments('-Wno-unused-result', language : 'c')

gtk = dependency ('gtk+-3.0')
samba =   dependency('smbclient')
cups = dependency('cups', version : '>= 1.4', required: false)
polkit = dependency('polkit-gobject-1', version: '>= 0.103')
gsettings = dependency('gsettings-desktop-schemas', version: '>= 42.alpha')

deps = [ gtk, samba, cups, polkit, gsettings ]

if meson.project_name().contains('rpcc')
  shared_module(meson.project_name(), sources, dependencies: deps, install: true,
        install_dir: get_option('libdir') / 'rpcc',
        c_args : '-DPLUGIN_NAME="' + meson.project_name() + '"'
  )
else
  executable (meson.project_name(), sources, dependencies: deps, install: true)
endif
