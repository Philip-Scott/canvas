project('com.github.akiraux.interactive-goocanvas', ['vala', 'c'],
    version: '0.2.0'
)

gnome = import('gnome')
i18n = import('i18n')

conf = configuration_data()
conf.set_quoted('GETTEXT_PACKAGE', meson.project_name())
configure_file(output: 'config.h', configuration: conf)
config_h_dir = include_directories('.')

cc = meson.get_compiler('c')
m_dep = cc.find_library('m', required: true)

add_project_arguments(['--vapidir', join_paths(meson.current_source_dir(), 'vapi')],
                      language: 'vala')

c_args = [
  '-include', 'config.h',
]

executable(
    'com.github.akiraux.interactive-goocanvas',
    'src/Application.vala',
    'src/HeaderBar.vala',
    'src/Window.vala',
    'src/ResponsiveCanvas.vala',
    c_args: c_args,
    dependencies: [
        dependency('glib-2.0'),
        dependency('gobject-2.0'),
        dependency('gtk+-3.0'),
        dependency('goocanvas-2.0'),
        m_dep,
    ],
    install : true
)

meson.add_install_script('meson/post_install.py')
