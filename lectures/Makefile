## This is 708/lectures

current: target
-include target.mk

-include makestuff/perl.def

vim_session:
	bash -cl "vmt"

######################################################################

## specific to lectures

Sources += $(wildcard pix/*.*)

pix:
	$(mkdir)

pix/%:
	$(MAKE) pix
	$(CP) nopix/$* $@

pardirs += code
hotdirs += code

## Dormant
slideous: dir=docs
slideous:
	$(linkdir)

######################################################################

Sources += $(wildcard *.R)

## lecture dependencies

docs/dim.notes.html docs/dim.slides.html: code/iris.ggp.png

docs/get_maps.notes.html docs/get_maps.slides.html: get_spatial_data.Rout

docs/spatial_ex.notes.html docs/spatial_ex.slides.html: get_spatial_data.Rout

get_spatial_data.Rout: get_spatial_data.R tdata/stamp
	$(pipeR)

docs/fake.notes.html docs/fake.slides.html: tdata/fake.rda

tdata/fake.Rout: fake.R tdata/stamp
	$(pipeR)

Ignore += tdata
tdata/stamp:
	- mkdir tdata
	touch $@

######################################################################

Sources += $(wildcard *.md)

## docs/ subdirectory here maps to a corresponding subdirectory in docs

Ignore += docs
include ../rweb.mk

######################################################################

Sources += $(wildcard *.txt *.tmp) md.fmt

Ignore += $(wildcard *.lmd)
%.lmd: %.txt %.tmp md.fmt makestuff/newtalk/lect.pl
	$(PUSHRO)

######################################################################

### Makestuff

Sources += Makefile

Ignore += makestuff
msrepo = https://github.com/dushoff

Makefile: makestuff/Makefile
makestuff/Makefile:
	cd .. && $(MAKE) makestuff
	ln -s ../makestuff .
	ls $@

-include makestuff/os.mk

-include makestuff/dmdeps.mk
-include makestuff/hotcold.mk
-include makestuff/webpix.mk
-include makestuff/pipeR.mk

-include makestuff/git.mk
-include makestuff/visual.mk

