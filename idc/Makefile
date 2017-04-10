NS = skepickle
REPO = jinkies
VERSION ?= latest

NAME = jinkies
INSTANCE = idc

GIT_BRANCH = $(shell git rev-parse --abbrev-ref HEAD)

.PHONY: build run attach logs rm default

build:
	docker build -t $(NS)/$(REPO):$(VERSION) .

run:
	docker run --env GIT_BRANCH=${GIT_BRANCH} --name $(NAME)-$(INSTANCE) -i -t $(NS)/$(REPO):$(VERSION)

attach:
	docker attach --sig-proxy=true $(NAME)-$(INSTANCE)

logs:
	docker logs $(NAME)-$(INSTANCE)

rm:
	docker rm   $(NAME)-$(INSTANCE)

default: build

