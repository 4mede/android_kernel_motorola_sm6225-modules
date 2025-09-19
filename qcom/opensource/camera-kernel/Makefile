# Makefile for use with Android's kernel/build system

KBUILD_OPTIONS += KERNEL_ROOT=$(KERNEL_SRC)
KBUILD_OPTIONS += MODNAME=camera
KBUILD_OPTIONS += CAMERA_KERNEL_ROOT=$(KERNEL_SRC)/$(M)
KBUILD_OPTIONS += BOARD_PLATFORM=bengal
KBUILD_OPTIONS += KBUILD_EXTRA_SYMBOLS=$(OUT_DIR)/../sm6225-modules/qcom/opensource/mmrm-driver/Module.symvers

ifneq (,$(filter y, $(CONFIG_BATHENA_DTB) $(CONFIG_BORNEO_DTB) $(CONFIG_CAPRI_DTB) $(CONFIG_CAPRIP_DTB) $(CONFIG_CEBU_DTB) $(CONFIG_GUAM_DTB) $(CONFIG_GUAMP_DTB) $(CONFIG_RHODE_DTB)))
LINUXINCLUDE    += \
		-include $(CAMERA_KERNEL_ROOT)/config/legacycameraconf.h
endif

all: modules

modules dtbs:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) modules $(KBUILD_OPTIONS)

modules_install:
	$(MAKE) M=$(M) -C $(KERNEL_SRC) modules_install

clean:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) clean
