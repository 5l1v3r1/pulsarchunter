#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.57)
AC_INIT([PulsarCHunter],[1.10],[mkeith@pulsarastronomy.net])

if test -n "${CXXFLAGS}"; then
	user_set_cxxflags=yes
fi

SWIN_OPTIONS_SET

AC_CONFIG_AUX_DIR([config])
#AC_CONFIG_SRCDIR([Makefile.am])
# Create static libraries by default
AC_DISABLE_SHARED

# Enable large-file support
AC_SYS_LARGEFILE

# Determine the machine endian
AC_C_BIGENDIAN

# Checks for programs.
AC_PROG_CXX
AC_PROG_CXXCPP
AC_PROG_CC
AC_PROG_CPP
AM_PROG_CC_C_O
AC_PROG_F77
AC_PROG_F77_C_O
AC_F77_LIBRARY_LDFLAGS

if test -n "${CXXFLAGS}"; then
	user_set_cxxflags=yes
fi
AC_PROG_CXX
if test X$user_set_cxxflags != Xyes; then
	CXXFLAGS="-O2"
fi


AC_PROG_INSTALL
AC_PROG_LIBTOOL

AM_PATH_XML2

MJK_LIB_PSRXML

if test X$have_psrxml != Xyes; then
	AC_ERROR("Need psrxml library to compile! Specify location with --with-psrxml-dir") 
fi

SWIN_LIB_FFTWf

if test X$have_fftw3f != Xyes; then
	AC_ERROR("Need single precision FFTW 3 library to compile (libfftw3f.a)! Specify location with --with-fftw-dir")
fi

CHECK_ZLIB


AC_SUBST(XML_CPPFLAGS)
AC_SUBST(PSRXML_LIBS)
AC_SUBST(PSRXML_CFLAGS)



AM_INIT_AUTOMAKE([foreign subdir-objects])

AM_CONFIG_HEADER([config.h])
AC_CONFIG_FILES([Makefile src/Makefile src/pch-tune/Makefile src/pch-seek/Makefile src/barycentre-sla/Makefile src/pch-dmcomp/Makefile])

AC_OUTPUT
