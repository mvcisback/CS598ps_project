SECTIONS = report.md
TEMPLATE = template.tex
OUTPUT = ./build/report.pdf
ENGINE = pdflatex
DISABLED_RULES=WHITESPACE_RULE,COMMA_PARENTHESIS_WHITESPACE,CURRENCY

all: paper

.PHONY: all clean

pre:
	mkdir -p build

post:
	@echo POST

clean:
	rm -rf build

paper: $(SECTIONS) pre
	pandoc --toc -N -o $(OUTPUT) --template=$(TEMPLATE) $(SECTIONS) --latex-engine=$(ENGINE)

test-grammar:
	languagetool -d $(DISABLED_RULES) $(SECTIONS)

test-spelling:
	aspell -c $(SECTIONS)

test: test-spelling test-grammar

default: paper
