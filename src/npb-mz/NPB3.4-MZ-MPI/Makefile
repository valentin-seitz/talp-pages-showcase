SHELL=/bin/sh
CLASS=W
VERSION=
SFILE=config/suite.def

default: header
	@ sys/print_instructions

BT-MZ: bt-mz
bt-mz: header
	cd BT-MZ; $(MAKE) CLASS=$(CLASS) VERSION=$(VERSION)

SP-MZ: sp-mz
sp-mz: header
	cd SP-MZ; $(MAKE) CLASS=$(CLASS)
		       
LU-MZ: lu-mz
lu-mz: header
	cd LU-MZ; $(MAKE) CLASS=$(CLASS) VERSION=$(VERSION)

# Awk script courtesy cmg@cray.com
suite:
	@ awk -f sys/suite.awk SMAKE=$(MAKE) $(SFILE) | $(SHELL)


# It would be nice to make clean in each subdirectory (the targets
# are defined) but on a really clean system this will won't work
# because those makefiles need config/make.def
clean:
	- rm -f core *~ */core */*~
	- rm -f */*.o */*.obj */*.exe */*.mod */*.a
	- rm -f */npbparams.h */mpinpb.f90
	- rm -f sys/setparams sys/makesuite sys/setparams.h

veryclean: clean
	- rm -f config/make.def config/suite.def Part*
	- rm -f bin/sp-mz.* bin/lu-mz.* bin/bt-mz.*

header:
	@ sys/print_header


