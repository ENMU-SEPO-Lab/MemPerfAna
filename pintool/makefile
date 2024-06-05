# Define PIN_TOOL to set the PATH
# define SET_PIN_TOOL
#    @echo "Updating PATH to include /home/imhmede/workspace/pin-3.30"
#    export PATH=$$PATH:/home/imhmede/workspace/pin-3.30
#    @echo "Updated PATH: $$PATH"
#endef

# Declare PIN_TOOL initially as empty
PIN_ROOT =
CONFIG_ROOT =

# Find pin tool

find_pin_tool:
	@echo "Setting PIN_TOOL"
    $(foreach dir,$(subst :, ,$(PATH)), \
        $(if $(wildcard $(dir)/pin), \
            $(eval PIN_ROOT := $(dir)) \
						$(eval CONFIG_ROOT := $(PIN_ROOT)/source/tools/Config) \
            $(info Found pin tool at $(dir)/pin) \
            $(shell exit) \
        ) \
    )
    $(if $(PIN_ROOT),,$(error Pin tool not found in PATH)i \ CONFIG_ROOT := ../Config)
	include $(CONFIG_ROOT)/makefile.config
	include makefile.rules
	include $(TOOLS_ROOT)/Config/makefile.default.rules

# Compile the cachesim_itf.so
cachesim_itf.so:
	make obj-intel64/cachesim_itf.so

# Example rule that uses PIN_TOOL
all: find_pin_tool cachesim_itf.so
	@echo "PIN_TOOL is currently set to: '$(PIN_ROOT)'"

