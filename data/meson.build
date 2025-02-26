if build_standalone
  install_data('piprint.ui', install_dir: ui_dir)
  i18n.merge_file(input: 'piprint.desktop.in',
    output: 'piprint.desktop',
    type: 'desktop',
    po_dir: '../po',
    install: true,
    install_dir: desktop_dir
  )
endif
