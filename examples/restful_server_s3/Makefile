PROG = restful_server_s3
SOURCES = $(PROG).c ../../fossa.c
CFLAGS = -W -Wall -I../.. $(CFLAGS_EXTRA)

ifeq ($(SSL), openssl)
	CFLAGS += -DNS_ENABLE_SSL -lssl -lcrypto -lcrypto
else ifeq ($(SSL), krypton)
	CFLAGS += -DNS_ENABLE_SSL ../../../krypton/krypton.c
endif

all: $(PROG)

$(PROG): $(SOURCES)
	$(CC) $(SOURCES) -o $@ $(CFLAGS)

$(PROG).exe: $(SOURCES)
	cl $(SOURCES) /I../.. /MD /DNS_ENABLE_THREADS /Fe$@ advapi32.lib

clean:
	rm -rf *.gc* *.dSYM *.exe *.obj *.o a.out $(PROG)
