# Makefile.am for common functions for openCryptoki
# Michael A. Halcrow <mhalcrow@us.ibm.com>

SUBDIRS=ccalibs

#
# The PKCS#11 STDLL library
#
nobase_lib_LTLIBRARIES=opencryptoki/stdll/libpkcs11_cca.la

# Not all versions of automake observe libname_CFLAGS
opencryptoki_stdll_libpkcs11_cca_la_CFLAGS = -DLINUX -DSPINXPL -DNOCDMF	\
	-DNODSA -DNODH -DNOECB						\
	-I. -I../../../include	-I../../../include/pkcs11 -I../common	\
	-DSTDLL_NAME=\"ccatok\"

# Not all versions of automake observe libname_CFLAGS
AM_CFLAGS = -DLINUX -DSPINXPL -DNOCDMF -DNODSA -DNODH -DNOECB		\
	-DNODSA -DNODH -DNOECB						\
	-I. -I../../../include	-I../../../include/pkcs11 -I../common	\
	-DSTDLL_NAME=\"ccatok\"

opencryptoki_stdll_libpkcs11_cca_la_LDFLAGS = -shared -Wl,-Bsymbolic	\
	-lcrypto -lpthread -nostartfiles -Wl,-soname,$@			\
	-Wl,-L./ccalibs/opencryptoki/stdll/.libs			\
	-Wl,-lcsulsecy -Wl,-lcsulcall -Wl,-lcsulsapi -Wl,-lds30

opencryptoki_stdll_libpkcs11_cca_la_SOURCES = ../common/asn1.c		\
					      ../common/dig_mgr.c	\
					      ../common/hwf_obj.c	\
					      ../common/log.c		\
					      ../common/key.c		\
					      mech_dh.c			\
					      ../common/mech_rng.c	\
					      new_host.c		\
					      sign_mgr.c		\
					      ../common/cert.c		\
					      ../common/dp_obj.c	\
					      mech_aes.c		\
					      mech_rsa.c		\
					      ../common/obj_mgr.c	\
					      ../common/template.c	\
					      ../common/data_obj.c	\
					      encr_mgr.c		\
					      ../common/key_mgr.c	\
					      ../common/mech_md2.c	\
					      mech_sha.c		\
					      ../common/object.c	\
					      decr_mgr.c		\
					      globals.c			\
					      loadsave.c		\
					      utility.c			\
					      mech_des.c		\
					      mech_des3.c		\
					      ../common/mech_md5.c	\
					      ../common/mech_ssl3.c	\
					      ../common/sess_mgr.c	\
					      verify_mgr.c		\
					      cca_specific.c

noinst_HEADERS = h_extern.h tok_spec_struct.h defs.h csulincl.h		\
		 host_defs.h cca_stdll.h tok_specific.h

install-data-local:
	mkdir -p -- "$(DESTDIR)/$(datadir)/opencryptoki"
	@INSTALL@ README-IBM_CCA_users $(DESTDIR)/$(datadir)/opencryptoki
