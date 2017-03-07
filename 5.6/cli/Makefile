.PHONY: all push

USER="501stalpha1"
ifeq ($(shell uname -m), i686)
  PLATFORM="686"
else
  PLATFORM="amd64"
endif
FULL_VERSION="5.6.30"
MINOR_VERSION=$(shell echo $(FULL_VERSION) | cut -d '.' -f -2)
MAJOR_VERSION=$(shell echo $(FULL_VERSION) | cut -d '.' -f 1)

all: .last-docker-build

.last-docker-build: Dockerfile
	docker build -t "$(USER)/php:$(FULL_VERSION)-cli-$(PLATFORM)" .
	docker tag "$(USER)/php:$(FULL_VERSION)-cli-$(PLATFORM)" "$(USER)/php:$(MINOR_VERSION)-cli-$(PLATFORM)"
	docker tag "$(USER)/php:$(FULL_VERSION)-cli-$(PLATFORM)" "$(USER)/php:$(MAJOR_VERSION)-cli-$(PLATFORM)"
	docker tag "$(USER)/php:$(FULL_VERSION)-cli-$(PLATFORM)" "$(USER)/php:latest-$(PLATFORM)"
	@touch $@

push: .last-docker-push

.last-docker-push: .last-docker-build
	docker push "$(USER)/php:$(FULL_VERSION)-cli-$(PLATFORM)"
	docker push "$(USER)/php:$(MINOR_VERSION)-cli-$(PLATFORM)"
	docker push "$(USER)/php:$(MAJOR_VERSION)-cli-$(PLATFORM)"
	docker push "$(USER)/php:latest-$(PLATFORM)"
	@touch $@
