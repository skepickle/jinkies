NS = skepickle
REPO = jinkies
VERSION ?= latest

NAME = jinkies
INSTANCE = idc

.PHONY: build run attach logs rm default

build:
	docker build -t $(NS)/$(REPO):$(VERSION) .

run:
	docker run           --name $(NAME)-$(INSTANCE) -i -t $(NS)/$(REPO):$(VERSION)

attach:
	docker attach --sig-proxy=true $(NAME)-$(INSTANCE)

logs:
	docker logs $(NAME)-$(INSTANCE)

rm:
	docker rm   $(NAME)-$(INSTANCE)

default: build

