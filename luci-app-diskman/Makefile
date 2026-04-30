# Copyright (C) 2016 Openwrt.org
include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-diskman
PKG_VERSION:=0.2.13
PKG_RELEASE:=1
PKG_MAINTAINER:=lisaac <https://github.com/lisaac/luci-app-diskman>
PKG_LICENSE:=AGPL-3.0

LUCI_TITLE:=Disk Manager interface for LuCI
LUCI_DESCRIPTION:=Disk Manager interface for LuCI

# 适配 25.12：
# 1. 移除了旧版 kmod-fs-ntfs，改为现代的 kmod-fs-ntfs3
# 2. 保持对基础工具的依赖
LUCI_DEPENDS:=+luci-compat +luci-lib-ipkg +e2fsprogs +parted +smartmontools +blkid \
	+kmod-fs-vfat +dosfstools +kmod-fs-msdos +kmod-nls-base +kmod-nls-utf8 \
	+kmod-nls-cp932 +kmod-nls-cp936 +kmod-nls-cp950 \
	+kmod-fs-exfat +exfat-mkfs +exfat-fsck \
	+kmod-fs-ntfs3 \
	+kmod-fs-btrfs \
	+PACKAGE_$(PKG_NAME)_INCLUDE_ntfs_3g_utils:ntfs-3g-utils \
	+PACKAGE_$(PKG_NAME)_INCLUDE_btrfs_progs:btrfs-progs \
	+PACKAGE_$(PKG_NAME)_INCLUDE_lsblk:lsblk \
	+PACKAGE_$(PKG_NAME)_INCLUDE_mdadm:mdadm \
	+PACKAGE_$(PKG_NAME)_INCLUDE_kmod_md_raid456:mdadm \
	+PACKAGE_$(PKG_NAME)_INCLUDE_kmod_md_raid456:kmod-md-raid456 \
	+PACKAGE_$(PKG_NAME)_INCLUDE_kmod_md_linears:mdadm \
	+PACKAGE_$(PKG_NAME)_INCLUDE_kmod_md_linears:kmod-md-linear

define Package/$(PKG_NAME)/config
config PACKAGE_$(PKG_NAME)_INCLUDE_ntfs_3g_utils
	depends on PACKAGE_$(PKG_NAME)
	bool "Include ntfs-3g-utils"
	default y
config PACKAGE_$(PKG_NAME)_INCLUDE_btrfs_progs
	depends on PACKAGE_$(PKG_NAME)
	bool "Include btrfs-progs"
	default y
config PACKAGE_$(PKG_NAME)_INCLUDE_lsblk
	depends on PACKAGE_$(PKG_NAME)
	bool "Include lsblk"
	default y
config PACKAGE_$(PKG_NAME)_INCLUDE_mdadm
	depends on PACKAGE_$(PKG_NAME)
	bool "Include mdadm"
	default n
config PACKAGE_$(PKG_NAME)_INCLUDE_kmod_md_raid456
	depends on PACKAGE_$(PKG_NAME)_INCLUDE_mdadm
	bool "Include kmod-md-raid456"
	default n
config PACKAGE_$(PKG_NAME)_INCLUDE_kmod_md_linears
	depends on PACKAGE_$(PKG_NAME)_INCLUDE_mdadm
	bool "Include kmod-md-linear"
	default n
endef

include $(TOPDIR)/feeds/luci/luci.mk

$(eval $(call BuildPackage,$(PKG_NAME)))
