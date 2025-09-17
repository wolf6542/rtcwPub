CC = gcc
CFLAGS = -m32 -O3 -fPIC -fsigned-char -DGAMEDLL
DCFLAGS = -m32 -g -fPIC -fsigned-char -DGAMEDLL
LDFLAGS = -m32 -shared -Wl,-V

SOURCES = $(shell ls g_*.c q_*.c ai_*.c bg_animation.c bg_misc.c bg_pmove.c bg_slidemove.c ../botai/*.c)
MODULES = $(SOURCES:.c=.o)

all: gameclean qagame.mp.i386.so

gameclean:
	rm -rf *.o ../botai/*.o

qagame.mp.i386.so: $(MODULES)
	$(CC) $(LDFLAGS) -Wl,-soname,$@ -o $@ $?

debug: CFLAGS := $(DCFLAGS)
debug: $(MODULES)
	$(CC) -m32 -shared -Wl,-soname,qagame.mp.i386_debug.so -o qagame.mp.i386_debug.so $?

.c.o:
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f *.o *.so ../botai/*.so ../botai/*.o
