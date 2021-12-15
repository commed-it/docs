FILES := $(shell ls | grep .puml)

all:
	@echo $(FILES)
	@for file in $(FILES) ; do \
		java -jar plantuml.jar $$file; \
	done
	@echo "Done"

