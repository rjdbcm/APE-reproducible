configure_file(input: 'ace_to_drs.pl', output: 'ace_to_drs.pl', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'ape_utils.pl', output: 'ape_utils.pl', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'fit_to_plp.pl', output: 'fit_to_plp.pl', install: true, install_dir: libpath / 'parser', copy: true)
plp_files = custom_target(
    command: ['swipl', '-g', 'working_directory(_, "prolog/parser"), [fit_to_plp], halt.'],
    output: ['grammar_contentwords.plp', 'grammar_functionwords.plp', 'grammar.plp', 'sorts.plp'],
    install: true,
    install_dir: libpath / 'parser',
)
grammar_doc = custom_target(
    build_by_default: true,
    capture: true,
    input: ['grammar.fit', 'grammar_functionwords.fit', 'grammar_contentwords.fit'],
    command: [cat, '@INPUT@'],
    install: true,
    install_dir: get_option('mandir') / project_folder,
    output: 'grammar.doc',
)
configure_file(input: 'make_syntax_report.perl', output: 'make_syntax_report.perl', install: true, install_dir: libpath / 'parser', copy: true)
custom_target(
    build_by_default: true,
    capture: true,
    command: [perl,
        'prolog/parser/make_syntax_report.perl',
        '--number', meson.project_version()
    ],
    feed: true,
    input: grammar_doc,
    output: 'syntax_report.html',
    install: true,
    install_dir: get_option('mandir') / project_folder,
)
configure_file(input: 'grammar_contentwords.fit', output: 'grammar_contentwords.fit', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'grammar_functionwords.fit', output: 'grammar_functionwords.fit', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'grammar.fit', output: 'grammar.fit', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'grammar_words.pl', output: 'grammar_words.pl', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'prologfeatures.pl', output: 'prologfeatures.pl', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'refres.pl', output: 'refres.pl', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'sentence_failure.pl', output: 'sentence_failure.pl', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'sorts.fit', output: 'sorts.fit', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'tokenizer.pl', output: 'tokenizer.pl', install: true, install_dir: libpath / 'parser', copy: true)
configure_file(input: 'tokens_to_sentences.pl', output: 'tokens_to_sentences.pl', install: true, install_dir: libpath / 'parser', copy: true)