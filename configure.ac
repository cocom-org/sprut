#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([Sprut], 0.97, [vmakarov@gcc.gnu.org])
AC_CONFIG_AUX_DIR([.])
AM_INIT_AUTOMAKE([foreign])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_SRCDIR([anal.c])
AM_MAINTAINER_MODE

# Checks for programs.
AC_PROG_CC
AC_PROG_CXX

# Checks for libraries.

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_SIZE_T

# Checks for library functions.
AC_FUNC_ERROR_AT_LINE
AC_FUNC_MALLOC
AC_FUNC_REALLOC
AC_CHECK_FUNCS([memmove memset strerror])

AC_PROG_YACC

AC_TYPE_SIGNAL

AC_CONFIG_FILES([Makefile])

AC_ARG_ENABLE([debug],
[  --enable-debug    Turn on debugging],
[case "${enableval}" in
      yes) cocom_debug=true ;;
       no)  cocom_debug= ;;
        *) AC_MSG_ERROR([bad value ${enableval} for --enable-debug]) ;;
      esac],[cocom_debug=])

if test x$cocom_debug = x; then
  c_debug_define=-DNDEBUG
else
  my_save_cflags="$CFLAGS"
  CFLAGS=-g3
  AC_MSG_CHECKING([whether CC supports -g3])
  AC_COMPILE_IFELSE([AC_LANG_PROGRAM([])],
      [AC_MSG_RESULT([yes])]
      [g3=yes],
      [AC_MSG_RESULT([no])]
  )
  CFLAGS="$my_save_cflags"

  if test "$g3" = yes; then
    CFLAGS='-O0 -g3'
    CXXFLAGS='-O0 -g3'
  else
    CFLAGS='-O0 -g'
    CXXFLAGS='-O0 -g'
  fi
  c_debug_define=
fi

CFLAGS="$CFLAGS $c_debug_define"
CXXFLAGS="$CXXFLAGS $c_debug_define"

AC_OUTPUT
