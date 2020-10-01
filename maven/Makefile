# Just a Makefile for manual testing
.PHONY: all

DOCKER_TAG=jenkins4eval/jenkinsfile-runner:maven
DOCKER_RUN_OPTS=-v maven-repo:/root/.m2
JDK_VERSION=8

all: clean build

clean:
	rm -rf tmp

.PHONY: docker
docker:
	docker build -t $(DOCKER_TAG) -f Dockerfile-jdk$(JDK_VERSION) .

build: docker

.PHONY: run
run:
	docker run --rm ${DOCKER_RUN_OPTS} \
	    -v $(shell pwd)/demo/simple/:/workspace/ \
	    $(DOCKER_TAG) 

.PHONY: demo
demo:
	docker run --rm ${DOCKER_RUN_OPTS} \
	    -v $(shell pwd)/demo/:/workspace/ \
	    $(DOCKER_TAG)

