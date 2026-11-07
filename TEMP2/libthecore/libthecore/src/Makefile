# [M2G]Soul - Modernized LibTheCore Makefile

CC = clang++
BIN_DIR = ../lib
BIN = $(BIN_DIR)/libthecore.a
INCLUDE = ../include

# C Flags
CFLAGS = -m32 -Wall -O3 -flto -pipe -g -I$(INCLUDE)
CFLAGS += -Wno-deprecated -Wno-invalid-source-encoding

# C++ Flags
CXXFLAGS = $(CFLAGS) -std=c++26

LIBS =

OBJFILES = socket.o fdwatch.o buffer.o signal.o log.o utils.o \
	kstbl.o hangul.o heart.o main.o tea.o des.o gost.o memcpy.o

default:
	$(MAKE) $(BIN)

$(BIN): $(OBJFILES)
	@if [ ! -d $(BIN_DIR) ]; then mkdir -p $(BIN_DIR); fi
	ar cru $(BIN) $(OBJFILES) $(LIBS)
	ranlib $(BIN)
	chmod 700 $(BIN)

clean:
	rm -f *.o
	rm -f $(BIN)

dep:
	touch Depend
	$(CC) $(CFLAGS) -MM *.c > Depend

%.o: %.c
	@echo compiling $<
	$(CC) $(CFLAGS) -c $< -o $@

include Depend