.PHONY: all push

USER="501stalpha1"
ifeq ($(shell uname -m), i686)
  PLATFORM="386"
else
  PLATFORM="amd64"
endif
FULL_VERSION="5.6.30"
MINOR_VERSION=$(shell echo $(FULL_VERSION) | cut -d '.' -f -2)
MAJOR_VERSION=$(shell echo $(FULL_VERSION) | cut -d '.' -f 1)

all: .last-docker-build

.last-docker-build: Dockerfile
	docker build -t "$(USER)/php:$(FULL_VERSION)-apache-$(PLATFORM)" .
	docker tag "$(USER)/php:$(FULL_VERSION)-apache-$(PLATFORM)" "$(USER)/php:$(MINOR_VERSION)-apache-$(PLATFORM)"
	docker tag "$(USER)/php:$(FULL_VERSION)-apache-$(PLATFORM)" "$(USER)/php:$(MAJOR_VERSION)-apache-$(PLATFORM)"
	docker tag "$(USER)/php:$(FULL_VERSION)-apache-$(PLATFORM)" "$(USER)/php:apache-$(PLATFORM)"
	@touch $@

push: .last-docker-push

.last-docker-push: .last-docker-build
	docker push "$(USER)/php:$(FULL_VERSION)-apache-$(PLATFORM)"
	manifest-tool push from-spec ./manifest-full.yml
	docker push "$(USER)/php:$(MINOR_VERSION)-apache-$(PLATFORM)"
	manifest-tool push from-spec ./manifest-minor.yml
	docker push "$(USER)/php:$(MAJOR_VERSION)-apache-$(PLATFORM)"
	manifest-tool push from-spec ./manifest-major.yml
	docker push "$(USER)/php:apache-$(PLATFORM)"
	@touch $@
