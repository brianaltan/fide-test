# files

EXE = fruit

OBJS = attack.o board.o book.o eval.o fen.o hash.o list.o main.o material.o \
       move.o move_check.o move_do.o move_evasion.o move_gen.o move_legal.o \
       option.o pawn.o piece.o posix.o protocol.o pst.o pv.o random.o recog.o \
       search.o search_full.o see.o sort.o square.o trans.o util.o value.o \
       vector.o

# rules

all: $(EXE) .depend

clean:
	$(RM) *.o .depend gmon.out $(EXE)

# general

CXX      = g++
CXXFLAGS = -pipe
LDFLAGS  = -lm

# C++ flags for size optimization

CXXFLAGS += -fno-exceptions -fno-rtti  # Disable exceptions and RTTI
CXXFLAGS += -Os                        # Optimize for size
CXXFLAGS += -fomit-frame-pointer       # Omit frame pointer for smaller code
CXXFLAGS += -ffunction-sections -fdata-sections  # Enable garbage collection of unused code
CXXFLAGS += -fno-asynchronous-unwind-tables  # Disable unwind tables
CXXFLAGS += -fno-stack-protector       # Disable stack protection
CXXFLAGS += -march=native              # Optimize for the current CPU architecture

# Linker flags for size optimization

LDFLAGS += -s                          # Strip all symbols
LDFLAGS += -Wl,--gc-sections           # Remove unused sections
LDFLAGS += -Wl,--strip-all             # Strip all symbols from the binary
LDFLAGS += -Wl,--as-needed             # Link only needed libraries

# dependencies

$(EXE): $(OBJS)
	$(CXX) $(LDFLAGS) -o $@ $(OBJS)

.depend:
	$(CXX) -MM $(OBJS:.o=.cpp) > $@

include .depend