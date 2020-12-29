# Per Platform
ifeq ($(CONFIG_MACH_MSM8998_JOAN),y)
DTS_PROJECT := msm8998-joan
endif

# Per Device
ifeq ($(CONFIG_MACH_MSM8998_JOAN_GLOBAL_COM),y)
DTS_TARGET := msm8998-joan_global_com
endif

ALL_DTS := $(notdir $(wildcard echo $(srctree)/$(src)/$(DTS_PROJECT)/$(DTS_TARGET)/*.dts))
dtb-y += $(patsubst %.dts,%.dtb,$(ALL_DTS))

DTB_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM_APPENDED_DTB_IMAGE_NAMES))
ifneq ($(DTB_NAMES),)
DTB_LIST := $(addsuffix .dtb,$(DTB_NAMES))
else
DTB_LIST := $(dtb-y)
endif

always  := $(addprefix ../,$(DTB_LIST))

$(obj)/../%.dtb: $(src)/$(DTS_PROJECT)/$(DTS_TARGET)/%.dts FORCE
	$(call if_changed_dep,dtc)

clean-files := *.dtb
