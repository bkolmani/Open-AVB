OPT=-O2
#CFLAGS=$(OPT) -Wall -W -Wno-parentheses -Wstrict-prototypes -Wmissing-prototypes -ggdb
CFLAGS=$(OPT) -Wall -W -Wno-parentheses -ggdb -D_GNU_SOURCE

CC=gcc
INCFLAGS=-I../common
#LDLIBS=-ligb -lpci
#LDFLAGS=-L../lib

all: mrpd mrpctl

VPATH = ../common

mrpd: mrpd.o mvrp.o msrp.o mmrp.o mrp.o parse.o

mrpctl: mrpctl.o

%.o: %.c
	$(CC) -c $(INCFLAGS) $(CFLAGS) -o $@  $<
%: %.o
	$(CC) $(LDFLAGS) $^ $(LDLIBS) -o $@

clean:
	rm -f `find . -name "*~" -o -name "*.[oa]" -o -name "\#*\#" -o -name TAGS -o -name core -o -name "*.orig"`
	rm mrpd mrpctl
	
indent:
	indent --linux-style mrpd.c mrpd.h mvrp.c mvrp.h msrp.c msrp.h mmrp.c mmrp.h mrp.c mrp.h \
		mrpw.c que.c que.h ../common/parse.c ../common/parse.h


