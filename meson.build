project('g-up', 'rust',
    version: '0.1.0',
    meson_version: '>= 0.62.0',
    default_options: ['warning_level=2', 'werror=false']
)

cargo = find_program('cargo')

# Ejecutar cargo en modo offline
custom_target('build-myapp',
    command: [cargo, 'build', '--release', '--offline'],
    build_by_default: true,
    output: 'g-up'
)

install_data('target/release/g-up', install_dir: get_option('bindir'))
