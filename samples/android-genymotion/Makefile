#include Makefile.inc
CFLAGS:= -m32
CFLAGS:= -lc -pie -fPIE -nostdlib
#ARCH := $(shell getconf LONG_BIT)
#CPP_FLAGS_32 := -m32 -Wall -I$(INC_DIR) #...  Some 32 specific compiler flags ...
#CPP_FLAGS_64 := -Wall -I$(INC_DIR)
#CPP_FLAGS_ARM_32 := -Wall -I$(INC_DIR)
#CPP_FLAGS_ARM_64 := -Wall -I$(INC_DIR)

#CPP_FLAGS := $(CPP_FLAGS_$(ARCH))  #... all the other flags ...

UNAME_M=$(shell uname -m)
#addr-info: $(OBJECTS)
#	$(CC) $(CFLAGS) $(OBJECTS) -o addr-info $(LDFLAGS)
#SUBDIRS=samples/x86 samples/x86-64 samples/arm-32
SRCS = 	$(wildcard *.c)
PROGS = $(patsubst %.c,%,$(SRCS))
OBJECTS = $(patsubst %.c,%.o,$(SRCS))
samples: $(PROGS)	
	#echo 'hi'
	#echo "hi"
	#echo "PRJCFLAGS:$(PRJCFLAGS)"
	#@echo uname -m: $(UNAME_M)
	#@echo $(filter x86%,$(UNAME_M))
	#@echo $(filter %OS,Linux Darwin SunOS FreeBSD GNU/kFreeBSD NetBSD OpenBSD GNU)
all:samples
%.o:
	@echo $@
show-src:
	@echo $(SRCS)
show-progs:
	@echo $(PROGS)
show-objects:
	@echo About to make distribution files
	@echo $(OBJECTS)
%: %.c
	$(CC) $(CPP_FLAGS) $(CFLAGS) $(PRJCFLAGS) -o $@ $< $(LDFLAGS)

ifeq ($(filter %i686,$(UNAME_M)),)
	$(error Compile this sample on intel)
endif
clean:
	rm -f $(PROGS) $(OBJECTS)

.PHONY: all install clean test
