configure_file(
    input: 'downloader.pl',
    output: 'downloader.pl',
    copy:true
)
run_command(['swipl', '-f', 'none', '-g', 'ensure_clex', '-t', 'halt', '-s', 'downloader.pl'], check: true)
# custom_target(
#     build_by_default: true,
#     command: ['swipl', '-f', 'none', '-g', 'download_acetexts', '-t', 'halt', '-s', 'tests/downloader.pl'],
#     install: true,
#     install_dir: 'tests',
#     output: 'acetexts.pl',
# )

configure_file(input: 'acetexts.pl', output: 'acetexts.pl', copy: true)
configure_file(input: 'clex_lexicon.pl', output: 'clex_lexicon.pl', copy: true)
configure_file(input: 'README.md', output: 'README.md', copy: true)
configure_file(input: 'rtest.bash', output: 'rtest.bash', copy: true)
test_ape = configure_file(input: 'test_ape.pl', output: 'test_ape.pl', copy: true)
test_apeexe = configure_file(input: 'test_apeexe.sh', output: 'test_apeexe.sh', copy: true)
test_drace = configure_file(input: 'test_drace.pl', output: 'test_drace.pl', copy: true)
configure_file(input: 'test_drace.sh', output: 'test_drace.sh', copy: true)
configure_file(input: 'test_ndrace.sh', output: 'test_ndrace.sh', copy: true)
test_drs_to_x = configure_file(input: 'test_drs_to_x.pl', output: 'test_drs_to_x.pl', copy: true)
configure_file(input: 'test_drs_to_tptp_out.sh', output: 'test_drs_to_tptp_out.sh', copy: true)
test_duration = configure_file(input: 'test_duration.pl', output: 'test_duration.pl', copy: true)
configure_file(input: 'test_duration.sh', output: 'test_duration.sh', copy: true)
test_everything = configure_file(input: 'test_everything.sh', output: 'test_everything.sh', copy: true)
configure_file(input: 'test_owlswrl.pl', output: 'test_owlswrl.pl', copy: true)
configure_file(input: 'test_owlswrl.sh', output: 'test_owlswrl.sh', copy: true)
configure_file(input: 'test_ruleml.sh', output: 'test_ruleml.sh', copy: true)
subdir('testruns')
#test('everything', test_everything, workdir: meson.current_build_dir(), timeout: -1)
test('ape', swipl, args: ['-f', 'test_ape.pl', '-g', 'main', '-t', 'halt', '-q'], workdir: meson.current_build_dir(), timeout: -1)
# test('apeexe', find_program('bash'), args: ['test_apeexe.sh'], workdir: meson.current_build_dir(), timeout: -1)
test('rtest', sh, args: ['rtest.bash'], workdir: meson.current_build_dir(), timeout: -1)
test('drace', sh, args: ['test_drace.sh'], workdir: meson.current_build_dir(), timeout: -1)
test('ndrace', sh, args: ['test_ndrace.sh'], workdir: meson.current_build_dir(), timeout: -1)
test('owlswrl', sh, args: ['test_owlswrl.sh'], workdir: meson.current_build_dir(), timeout: -1)
test('drs_to_tptp_out', sh, args: ['test_drs_to_tptp_out.sh'], workdir: meson.current_build_dir(), timeout: -1)
benchmark('duration', sh, args: ['test_duration.sh'], workdir: meson.current_build_dir(), timeout: -1)