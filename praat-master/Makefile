# File: Makefile

# Makefile for Praat.
# Paul Boersma, 24 May 2020
# David Weenink, 22 December 2020

# System-dependent definitions of CC, LIBS, ICON and MAIN_ICON should be in
# makefile.defs, which has to be copied and renamed
# from a suitable makefile.defs.XXX file in the makefiles directory,
# Perhaps that file requires some editing.
include makefiles/makefile.defs.mingw64 ./makefile.defs

.PHONY: test all clean install

# Makes the Praat executable in the source directory.
#all-external all-self
all: 
	$(LINK) -o $(EXECUTABLE) main/main_Praat.o $(MAIN_ICON) fon/libfon.a \
		artsynth/libartsynth.a FFNet/libFFNet.a \
		gram/libgram.a EEG/libEEG.a \
		LPC/libLPC.a dwtools/libdwtools.a \
		fon/libfon.a stat/libstat.a dwsys/libdwsys.a \
		sys/libsys.a melder/libmelder.a kar/libkar.a \
		external/espeak/libespeak.a \
		external/portaudio/libportaudio.a \
		external/flac/libflac.a external/mp3/libmp3.a \
		external/glpk/libglpk.a \
		external/clapack/libclapack.a \
		external/gsl/libgsl.a \
		external/vorbis/libvorbis.a \
		external/opusfile/libopusfile.a \
		$(LIBS)

all-external:
	$(MAKE) -C external/clapack
	$(MAKE) -C external/gsl
	$(MAKE) -C external/glpk
	$(MAKE) -C external/mp3
	$(MAKE) -C external/flac
	$(MAKE) -C external/portaudio
	$(MAKE) -C external/espeak
	$(MAKE) -C external/vorbis
	$(MAKE) -C external/opusfile

all-self:
	$(MAKE) -C kar
	$(MAKE) -C melder
	$(MAKE) -C sys
	$(MAKE) -C dwsys
	$(MAKE) -C stat
	$(MAKE) -C fon
	$(MAKE) -C dwtools
	$(MAKE) -C LPC
	$(MAKE) -C EEG
	$(MAKE) -C gram
	$(MAKE) -C FFNet
	$(MAKE) -C artsynth
	$(MAKE) -C main main_Praat.o $(ICON)

clean: clean-external clean-self
	$(RM) praat

clean-external:
	$(MAKE) -C external/clapack clean
	$(MAKE) -C external/gsl clean
	$(MAKE) -C external/glpk clean
	$(MAKE) -C external/mp3 clean
	$(MAKE) -C external/flac clean
	$(MAKE) -C external/portaudio clean
	$(MAKE) -C external/espeak clean
	$(MAKE) -C external/vorbis clean
	$(MAKE) -C external/opusfile clean

clean-self:
	$(MAKE) -C kar clean
	$(MAKE) -C melder clean
	$(MAKE) -C sys clean
	$(MAKE) -C dwsys clean
	$(MAKE) -C stat clean
	$(MAKE) -C fon clean
	$(MAKE) -C dwtools clean
	$(MAKE) -C LPC clean
	$(MAKE) -C EEG clean
	$(MAKE) -C gram clean
	$(MAKE) -C FFNet clean
	$(MAKE) -C artsynth clean
	$(MAKE) -C main clean


install:
	$(INSTALL)


#--------Added Code for incremental Build---------#

# open cygwin, navigate to praat/ and then execute the command "***make build_all***" to compile all the modules at once.
# If changes are made to C files, the command above would still work, but if headers are changed, we have to execute clean command to delete all the object files.




build_all: melder_build artsynth_build fon_build FFNet_build gram_build EEG_build LPC_build dwtools_build dwsys_build stat_build kar_build sys_build external_build all

#-------For Building Individual modules-------#
melder_build:
	cd melder/ && make all
artsynth_build:
	cd artsynth/ && make all
fon_build:
	cd fon/ && make all
FFNet_build:
	cd FFNet/ && make all
gram_build:
	cd gram/ && make all
EEG_build:
	cd EEG/ && make all
LPC_build:
	cd LPC/ && make all
dwtools_build:
	cd dwtools/ && make all
dwsys_build:
	cd dwsys/ && make all
stat_build:
	cd stat/ && make all
kar_build:
	cd kar/ && make all
sys_build:
	cd sys/ && make all
testscript_build:
	praat testPRAATscript.psc testAUDIOfile.wav
temp:
	praat ../test_scripts/testPRAATscript.psc ../test_scripts/testAUDIOfile.wav
external_build:
	cd external/clapack/ && make all
	cd external/espeak/ && make all
	cd external/flac/ && make all
	cd external/glpk/ && make all
	cd external/gsl/ && make all
	cd external/mp3/ && make all
	cd external/opusfile/ && make all
	cd external/portaudio/ && make all
	cd external/vorbis/ && make all

