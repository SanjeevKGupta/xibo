#
# Makefile : ianw
# -------------------------------------------------------

# Check all necessary environment variables
-include ../../env.check.mk

export ARCH ?= $(shell hzn architecture)

# Import variables from hzn.json (file is generated by last target in this file)
-include .hzn.json.tmp.mk

all: publish-service deploy-policy

# Publish a Horizon service (per service.json) and pull image to get its sha256
publish-service:
	hzn exchange service publish -O -f horizon/service.definition.json --pull-image

publish-pattern:
	hzn exchange pattern publish -f horizon/$(IMAGE_NAME).pattern.json

deploy-policy:
	hzn exchange deployment addpolicy -f horizon/deploy_policy_$(IMAGE_NAME).json deploy_$(EDGE_OWNER).$(EDGE_DEPLOY).$(IMAGE_NAME)_$(ARCH)

# This imports the variables from hzn.json
.hzn.json.tmp.mk: horizon/hzn.json
	@ hzn util configconv -f $< > $@
