project = ../bin/asm
objects = assembler.tab.c lex.yy.c
hfiles = $(wildcard *.h)
cfiles = $(filter-out $(objects), $(wildcard *.c))

.PHONY: all clean

all: $(project)

$(project) : $(objects) $(cfiles) $(hfiles)
	gcc -o $@ $(objects) $(cfiles)

assembler.tab.c : assembler.y 
	bison -d $<

lex.yy.c : assembler.lex assembler.tab.h
	flex $<

clean :
	rm -f assembler.tab.c assembler.tab.h lex.yy.c $(project) $(project:=.exe)

# This rule keeps Make happy, while the %.tab.h file is generated by
#  the bison rule above
%.tab.h: %.tab.c
	if [ -e $@ ]; then touch $@; else false; fi
