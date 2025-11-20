project('APE', version: '6.7', license: 'LGPL-3.0-only', license_files: 'LICENSE.txt')
perl = find_program('perl', required: true)
cat = find_program('cat', required: true)
xxd = find_program('xxd', required: true)
swipl = find_program('swipl', required: true)
sh = find_program('sh', required: true)
project_folder = '@0@-@1@'.format(meson.project_name(), meson.project_version())
libpath = get_option('libdir') / project_folder / 'prolog'
subdir('prolog')
configure_file(input: 'ape.pl', output: 'ape.pl', copy: true)
configure_file(input: 'pack.pl', output: 'pack.pl', copy: true)
configure_file(input: 'runape.pl', output: 'runape.pl', copy: true)
ape_exe = custom_target(
    command: [swipl, '-O', '-f',  '@BUILD_ROOT@' / 'ape.pl', '-g', 'qsave_program("@OUTPUT@", [goal(ape), toplevel(halt), stand_alone(true)]).', '-t', 'halt'],
    depends: plp_files,
    install: true,
    install_dir: get_option('bindir'),
    output: 'ape.exe',
)
custom_target(
    command: [swipl, '-O', '-f',  '@BUILD_ROOT@' / 'runape.pl', '-g', 'qsave_program("@OUTPUT@", [stand_alone(true)]).', '-t', 'halt'],
    depends: plp_files,
    install: true,
    install_dir: get_option('bindir'),
    output: 'ape.cmd',
)
subdir('tests')
