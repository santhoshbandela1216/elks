BASEDIR=..

include $(BASEDIR)/Make.defs

###############################################################################
#
# Include standard packaging commands.

include $(BASEDIR)/Make.rules

HOSTCC = gcc
HOST_CFLAGS = -O2

###############################################################################

PRGS=ed tar compress uncompress zcat miniterm
PRGS_HOST=compress.host

LOCALFLAGS=-H0xe000

all: $(PRGS) $(PRGS_HOST)

compress: compress.c

compress.host: compress.c
	$(HOSTCC) $(HOST_CFLAGS) -s compress.c -o $@

uncompress: compress
	ln -sf compress uncompress

zcat: compress
	ln -sf compress zcat

install: $(PRGS)
	sudo install $(PRGS) $(TARGET_MNT)/usr/bin

clean:
	rm -f $(PRGS) $(PRGS_HOST) *~ *.o
