# Usage:
# make        # compile all binary
# make clean  # remove ALL binaries and objects

.DEFAULT_GOAL := all
.PHONY: all clean

CC = gcc
CFLAGS = --std=c99 -g -Wall -Wextra -Werror

DEPS := hello.h
OBJ := hello.o func.o
BINS := hello
VALGRIND := valgrind

# Functions and Patterns
# SRCS := $(wildcard *.c)
# OBJ := $(SRCS:%.c=%.o)

all: $(BINS)

%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

hello: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS)

clean:
	rm -f *.o $(BINS)
	rm -f discussion.log

# compiles and runs the executable
run: hello 
	./hello

# compiles and runs the executable with valgrind
valgrind: hello 
	$(VALGRIND) ./hello

# compiles and runs the executable, checks against an expected output
check: hello 
	./hello > hello.tmp
	-diff hello.tmp hello.out

# get the git log
log: 
	git log > discussion.log

# looks at status of the repo
status: 
	@make clean 
	git branch
	git status 

# download files from the code repo
pull:
	@make clean
	git pull
	git status

# repeats your message back to you!
# usage: make chirp MSG="...."
chirp:
	@echo "Polly wants a cracker!"
	@echo $(MSG)
	@echo "Cya!"
