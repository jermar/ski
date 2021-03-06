## Process this file with automake to produce makefile.in
##
##
## Copyright (C) 1995-2007, Hewlett-Packard Development Company, L.P.
##
## This program is free software; you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published by
## the Free Software Foundation; either version 2 of the License, or 
## (at your option) any later version.
##
## This program is distributed in the hope that it will be useful, 
## but WITHOUT ANY WARRANTY; without even the implied warranty of 
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the 
## GNU General Public License for more details.
##
## You should have received a copy of the GNU General Public License along
## with this program; if not, write to the Free Software Foundation, Inc.,
## 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
##
##


SUBDIRS= decoder encoder fake-xterm

AM_CPPFLAGS= $(INCLTDL) $(X_CFLAGS) $(DWARF_CFLAGS) -I$(srcdir)/decoder \
			 -I$(srcdir)/encoder -I$(top_builddir)/src/encoder \
			 -I$(top_builddir)/src/decoder $(GSKI_CFLAGS) \
			 -DSKI_DATA_DIR=\"$(pkgdatadir)\"

lib_LTLIBRARIES=libski.la

bin_PROGRAMS= ski

ENCODING_FILES= \
	encodings/encoding.decode \
	encodings/encoding.encode \
	encodings/encoding.format \
	encodings/encoding.imm \
	encodings/encoding.opcode \
	encodings/encoding.unusedop

noinst_SCRIPTS= \
	asm.awk \
	das.awk \
	mkfns.awk \
	opcode.awk \
	combfns.awk \
	fmtimm.awk \
	mkicnt.awk \
	predecode.awk \
	iaexec_dec.sed \
	iadas_dec.sed \
	ia_types.sed \
	make_asm

noinst_DATA= \
	execTbl \
	$(ENCODING_FILES) \
	Copyright

gskidir= $(datadir)/ski
gski_DATA= \
	gski.glade

COMBFNS_FILES= \
	exec.c \
	fp_exec.c \
	mem_exec.c \
	mm_exec.c \
	read.c \
	sys_exec.c \
	write.c

COMBFNS_DERIVED= \
	combfns.h combfns.c

PREDECODE_DERIVED= \
	predecode.c \
	predecode.h \
	immed.h

IAEXEC_DECODER_DERIVED= \
	iaexec_decoder.c

IADAS_DECODER_DERIVED= \
	iadas_decoder.c

IADAS_TYPES_DERIVED= \
	iadas_types.h

DAS_INSTR_DERIVED= \
	das_instr.c

ASM_HASH_DERIVED= \
	asm_hash.c

ICNT_DERIVED= \
	icnt_core.h \
	icnt_ui.h

if WITH_NETDEV
NETDEV_C=netdev.c
else
NETDEV_C=
endif

BUILT_SOURCES= \
	$(COMBFNS_DERIVED) \
	$(PREDECODE_DERIVED) \
	$(IAEXEC_DECODER_DERIVED) \
	$(IADAS_DECODER_DERIVED) \
	$(IADAS_TYPES_DERIVED) \
	$(DAS_INSTR_DERIVED) \
	$(ASM_HASH_DERIVED) \
	$(ICNT_DERIVED) \
	instr.c

ski_SOURCES= \
	main.c

if HPUX
# on HPUX libtool does not work w/ -all-static
ski_LDFLAGS=-static
else
ski_LDFLAGS=-all-static
endif

if LINUX
# Debian wants everything to be dynamically linked
ski_LDFLAGS = 
endif

ski_LDADD= libski.la -ldl

skiincludedir= $(includedir)/ski-$(SKI_MAJOR_VERSION).$(SKI_MINOR_VERSION)
skiinclude_HEADERS= \
	asm.h \
	bits.h \
	coreui.h \
	exportui.h \
	fields.h \
	libcore.h \
	libsym.h \
	simmem.h \
	os_support.h \
	platform.h \
	sim.h \
	ski.h \
	state.h \
	std.h \
	types.h

noinst_HEADERS= \
	tlb.h \
	instinfo.h \
	sign_ext.h \
	interruption.h \
	ia_types.h \
	ia_state.h \
	ia_exec.h \
	ssc.h \
	float.h \
	ia_read.h \
	ia_write.h \
	libtrace.h \
	trace.h \
	instr.h \
	ia_decoder.h \
	package.h \
	libsrs.h \
	lp64struct.h \
	libui.h \
	memui.h \
	ia_das.h \
	das_instr.h \
	ssDCmd.h \
	lm.h \
	data.h \
	dos.h \
	program.h \
	eparse.h \
	libdas.h \
	netdev.h \
	osload.h \
	ltdl.h

EXTRA_linux_FILES = \
	linux/dwarf-linux.c \
	linux/osload-linux.c \
	linux/syscall-linux.c \
	linux/syscall-linux.h

if LINUX
linux_FILES = $(EXTRA_linux_FILES)
else
linux_FILES =
endif

EXTRA_hpux_FILES = \
	hpux/dwarf-hpux.c \
	hpux/osload-hpux.c \
	hpux/syscall-hpux.c \
	hpux/syscall-hpux.h

if HPUX
hpux_FILES = $(EXTRA_hpux_FILES)
else
hpux_FILES =
endif

EXTRA_freebsd_FILES = \
	freebsd/convert.c \
	freebsd/dwarf.c \
	freebsd/firmware.c \
	freebsd/machdep.h \
	freebsd/misc.c \
	freebsd/osload.c \
	freebsd/signal.c \
	freebsd/ssc.c \
	freebsd/syscall.c \
	freebsd/syscall.h

if FREEBSD
freebsd_FILES = $(EXTRA_freebsd_FILES)
else
freebsd_FILES =
endif

libski_la_SOURCES= \
	$(COMBFNS_DERIVED) \
	$(PREDECODE_DERIVED) \
	$(IAEXEC_DECODER_DERIVED) \
	$(ICNT_DERIVED) \
	state.c \
	sim.c \
	simmem.c \
	float.c \
	interruption.c \
	tlb.c \
	ia_read.c \
	ia_exec.c \
	ia_write.c \
	dos.c \
	memui.c \
	trace.c \
	libtrace.c \
	impl.c \
	os_support.c \
	ski_hook.c \
	instr.c \
	$(NETDEV_C) \
	$(linux_FILES) \
	$(hpux_FILES) \
	$(freebsd_FILES) \
	libsym.c \
	$(ASM_HASH_DERIVED) \
	$(IADAS_DECODER_DERIVED) \
	$(IADAS_TYPES_DERIVED) \
	$(DAS_INSTR_DERIVED) \
	ski.c \
	menu.c \
	ssDBT.c \
	ssDDM.c \
	ssDCmd.c \
	program.c \
	data.c \
	ssDSym.c \
	ssDPrs.c \
	traceui.c \
	ia_das.c \
	ui.c \
	batch.c \
	cur.c \
	ssX.c \
	ssXDSD.c \
	ssGtk.c \
	asm.c \
	version.c \
	eparse.y \
	escan.l \
	load.c \
	ltdl.c \
	platform.c \
	libdas.c \
	libsrs.c

EXTRA_libski_la_SOURCES = \
	$(EXTRA_linux_FILES) \
	$(EXTRA_hpux_FILES) \
	$(EXTRA_freebsd_FILES) \
	netdev.c 

libski_la_LDFLAGS = \
	-thread-safe -no-undefined \
	-version-info $(LT_CURRENT):$(LT_REVISION):$(LT_AGE) \
	-release $(LT_RELEASE) \
	-export-dynamic

libski_la_LIBADD= encoder/libencoder.la decoder/libdecoder.la $(LIBLTDL) \
	$(DWARF_LIBS) $(X_INTERFACE_LIBS) $(GSKI_LIBS)

EXTRA_DIST= \
	exec_hd.c \
	ia_decoder.c \
	missing/ski_elf.h \
	$(COMBFNS_FILES) \
	$(gski_DATA) \
	$(noinst_DATA) \
	$(noinst_SCRIPTS)

if WITH_X_INTERFACE
XSKI= xski
else
XSKI=
endif

if WITH_GTK_INTERFACE
GSKI= gski
else
GSKI=
endif

all-local: bski $(XSKI) $(GSKI)

bski $(XSKI) $(GSKI) : ski
	@rm -f $@; ln ski $@

## DERIVED sources rules:

das_instr.c: das.awk $(encdir)/encoding.opcode \
			 $(encdir)/encoding.unusedop \
			 $(srcdir)/libdas.c $(srcdir)/Copyright
	@rm -f $(DAS_INSTR_DERIVED)
	$(AWK) -v prefix=$(srcdir)/ -f $(srcdir)/das.awk \
		$(encdir)/encoding.opcode \
		unused=1 $(encdir)/encoding.unusedop

icnt_ui.h: icnt_core.h
icnt_core.h: mkicnt.awk $(encdir)/encoding.opcode \
				 $(encdir)/encoding.unusedop \
				 $(srcdir)/Copyright
	@rm -f $(ICNT_DERIVED)
	$(AWK) -v prefix=$(srcdir)/ -f $(srcdir)/mkicnt.awk \
		$(encdir)/encoding.opcode \
		unused=1 $(encdir)/encoding.unusedop
	touch icnt_ui.h

asm_hash.c: $(encdir)/encoding.opcode \
			asm.awk make_asm $(srcdir)/Copyright
	@rm -f $(ASM_HASH_DERIVED)
	sh $(srcdir)/make_asm -p $(encdir) -e /dev/null

iaexec_decoder.c: $(srcdir)/ia_decoder.c $(srcdir)/iaexec_dec.sed
	@rm -f $(IAEXEC_DECODER_DERIVED)
	sed -f $(srcdir)/iaexec_dec.sed $(srcdir)/ia_decoder.c > iaexec_decoder.c

iadas_decoder.c: $(srcdir)/ia_decoder.c $(srcdir)/iadas_dec.sed
	@rm -f $(IADAS_DECODER_DERIVED)
	sed -f $(srcdir)/iadas_dec.sed $(srcdir)/ia_decoder.c > iadas_decoder.c

iadas_types.h: $(srcdir)/ia_types.h $(srcdir)/ia_types.sed
	@rm -f $(IADAS_TYPES_DERIVED)
	sed -f $(srcdir)/ia_types.sed $(srcdir)/ia_types.h > iadas_types.h

combfns.h: combfns.c
combfns.c: execTbl $(COMBFNS_FILES) mkfns.awk combfns.awk
	@(rm -rf ./temp; mkdir temp; rm -f $(COMBFNS_DERIVED))
	$(AWK) -v prefix=$(srcdir)/ -f $(srcdir)/mkfns.awk \
		$(srcdir)/exec.c \
		$(srcdir)/fp_exec.c \
		$(srcdir)/mem_exec.c \
		$(srcdir)/mm_exec.c \
		$(srcdir)/read.c \
		$(srcdir)/sys_exec.c \
		$(srcdir)/write.c
	$(AWK) -v prefix=$(srcdir)/ -f $(srcdir)/combfns.awk \
		$(srcdir)/execTbl
	@touch combfns.h
	@rm -rf ./temp

predecode.h: predecode.c
immed.h: predecode.c
predecode.c: $(encdir)/encoding.format $(encdir)/encoding.imm \
			 fmtimm.awk predecode.awk $(srcdir)/Copyright
	@rm -rf $(PREDECODE_DERIVED)
	$(AWK) -v encdir=$(encdir) -f $(srcdir)/fmtimm.awk \
		$(encdir)/encoding.format | \
		$(AWK) -v prefix=$(srcdir)/ -f $(srcdir)/predecode.awk -
	@touch predecode.h immed.h

instr.c: $(encdir)/encoding.opcode \
		 $(encdir)/encoding.unusedop \
		 opcode.awk execTbl $(srcdir)/Copyright
	@rm -f instr.c
	$(AWK) -v prefix=$(srcdir)/ \
		-f $(srcdir)/opcode.awk $(encdir)/encoding.opcode \
		unused=1 $(encdir)/encoding.unusedop

eparse.h: eparse.c

distclean-local:
	-rm -f $(XSKI) $(GSKI) bski $(BUILT_SOURCES)
