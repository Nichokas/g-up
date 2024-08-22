project(
  'g-up', 'rust',
  version: '0.1.0',
  meson_version: '>= 0.62.0',
  default_options: ['warning_level=2', 'werror=false']
)

# Encuentra los programas necesarios
cargo = find_program('cargo', required: true)
cargo_generator = find_program('utils/flatpak-cargo-generator.py')

# Generar el archivo generated-sources.json usando el script
generated_sources = custom_target('generate-sources',
    output: 'generated-sources.json',
    command: [cargo_generator, 'Cargo.lock', 'generated-sources.json'],
    build_by_default: true
)

# Construir el proyecto usando cargo en modo offline
cargo_build = custom_target('cargo-build',
    input: generated_sources,
    output: ['g-up'],
    command: [cargo, 'build', '--release', '--offline'],
    build_by_default: true
)

# Instalar el binario resultante
install_data('target/release/g-up', install_dir: get_option('bindir'))
