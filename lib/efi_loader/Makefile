# SPDX-License-Identifier: GPL-2.0+
#
# (C) Copyright 2016 Alexander Graf
#

# This file only gets included with CONFIG_EFI_LOADER set, so all
# object inclusion implicitly depends on it

CFLAGS_efi_boottime.o += \
  -DFW_VERSION="0x$(VERSION)" \
  -DFW_PATCHLEVEL="0x$(PATCHLEVEL)"
CFLAGS_helloworld.o := $(CFLAGS_EFI) -Os -ffreestanding
CFLAGS_REMOVE_helloworld.o := $(CFLAGS_NON_EFI) -Os

ifneq ($(CONFIG_CMD_BOOTEFI_HELLO_COMPILE),)
always += helloworld.efi
endif

obj-$(CONFIG_CMD_BOOTEFI_HELLO) += helloworld_efi.o
obj-y += efi_image_loader.o efi_boottime.o efi_runtime.o efi_console.o
obj-y += efi_memory.o efi_device_path_to_text.o efi_device_path.o
obj-y += efi_device_path_utilities.o efi_file.o efi_variable.o efi_bootmgr.o
obj-y += efi_watchdog.o
obj-$(CONFIG_LCD) += efi_gop.o
obj-$(CONFIG_DM_VIDEO) += efi_gop.o
obj-$(CONFIG_PARTITIONS) += efi_disk.o
obj-$(CONFIG_NET) += efi_net.o
obj-$(CONFIG_GENERATE_ACPI_TABLE) += efi_acpi.o
obj-$(CONFIG_GENERATE_SMBIOS_TABLE) += efi_smbios.o
