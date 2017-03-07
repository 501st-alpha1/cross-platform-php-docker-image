.PHONY: all

USER="501stalpha1"
ifeq ($(shell uname -m), "i686")
  PLATFORM="686"
else
  PLATFORM="amd64"
endif

all: .last-docker-build

.last-docker-build: Dockerfile
	docker build -t "$(USER)/php:5.6-cli-$(PLATFORM)" .
	docker tag "$(USER)/php:5.6-cli-$(PLATFORM)" "$(USER)/php:5-cli-$(PLATFORM)"
	docker tag "$(USER)/php:5.6-cli-$(PLATFORM)" "$(USER)/php:latest-$(PLATFORM)"
	@touch $@
