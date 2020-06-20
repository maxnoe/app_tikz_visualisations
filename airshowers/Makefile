TEXOPTIONS = --lualatex --output-directory=build --interaction=nonstopmode --halt-on-error


NAMES=$(addprefix build/, gamma gamma_de cosmic_ray cosmic_ray_de)
EXTS=.pdf .png .svg


all: $(foreach ext, ${EXTS}, $(addsuffix ${ext}, ${NAMES}))


build/%_de.pdf: FORCE
	latexmk $(TEXOPTIONS) --jobname=$*_de $*.tex


build/%.pdf: FORCE
	latexmk $(TEXOPTIONS) $*.tex

build/%.png: build/%.pdf
	inkscape $< --export-dpi=600 -o $@

build/%.svg: build/%.pdf
	inkscape $< --export-plain-svg --export-text-to-path -o $@

clean:
	rm -rf build


.PHONY: all clean FORCE
