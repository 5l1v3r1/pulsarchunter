bin_PROGRAMS=pch-seek pch-seek-test
AM_CPPFLAGS=@PSRXML_CFLAGS@ @FFTWf_CFLAGS@

core_src=pch-seek.h toolkit.h TKfit.h gtools.h pch-seek-init.C pch-seek-read-file.C pch-seek-output.C pch-seek-do-search.C pch-seek-fourier.C pch-seek-phase-fit.C pch-seek-normalise.C pch-seek-harmfold-powtwo.C pch-seek-harmfold.C pch-seek-search-spec.C pch-seek-recon.C  pch-seek-singlepulse.C TKfit.C gtools.C toolkit.C pch-fourier-size.C pch-seek-options.h pch-seek-options.C pch-seek-zap.C

pch_seek_SOURCES=pch-seek.C $(core_src)
pch_seek_LDADD=@PSRXML_LIBS@ @FFTWf_LIBS@

pch_seek_test_SOURCES=pch-seek-test.C $(core_src)
pch_seek_test_LDADD=@PSRXML_LIBS@ @FFTWf_LIBS@


pch-seek.C: pch-seek-options.h pch-seek-harmfold-powtwo.C

pch-seek-harmfold-powtwo.C: make_harmfold_code.py
	python make_harmfold_code.py > pch-seek-harmfold-powtwo.C

pch-seek-options.C pch-seek-options.h: options.file make_options_code.py
	python make_options_code.py

MOSTLYCLEANFILES=pch-seek-harmfold-powtwo.C pch-seek-options.h pch-seek-options.C

EXTRA_DIST=options.file make_options_code.py make_harmfold_code.py
