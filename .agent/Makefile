THREADS ?= $(shell nproc)
ifeq ($(shell [ $(THREADS) -gt 8 ] && echo yes),yes)
THREADS := 8
endif

.PHONY: all clones lint libmacaroons

all: libmacaroons

clones:

lint:
	./check.sh

libmacaroons:
	cd .. && autoreconf -i
	cd .. && ./configure --prefix=/opt/libmacaroons
	$(MAKE) -C .. -j$(THREADS)
	$(MAKE) -C .. check
