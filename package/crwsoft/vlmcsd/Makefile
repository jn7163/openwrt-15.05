#
# Copyright (C) 2015 OpenWrt-dist
# Copyright (C) 2016 Chen RuiWei <crwbak@gmail.com>
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=vlmcsd
PKG_VERSION:=svn1016
PKG_RELEASE=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/Wind4/vlmcsd
PKG_SOURCE_VERSION:=0b2c216c06d7128422d9cd65cc6c9e3cfdfcefc6

PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Chen RuiWei <crwbak@gmail.com>

PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/vlmcsd
	SECTION:=net
	CATEGORY:=Extra packages
	TITLE:=vlmcsd for OpenWRT
	URL:=https://github.com/Wind4/vlmcsd
	DEPENDS:=+libpthread
endef

define Package/vlmcsd/description
vlmcsd is a KMS Emulator in C.
endef

define Package/vlmcsd/conffiles
/etc/config/vlmcsd
endef

MAKE_FLAGS += -C $(PKG_BUILD_DIR)

define Package/vlmcsd/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc/init.d $(1)/usr/share/vlmcsd $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/vlmcsd $(1)/usr/bin/
	$(INSTALL_BIN) ./files/vlmcsd.init $(1)/etc/init.d/vlmcsd
	$(INSTALL_DATA) ./files/vlmcsd.ini $(1)/usr/share/vlmcsd/
	$(INSTALL_DATA) ./files/vlmcsd.config $(1)/etc/config/vlmcsd
endef

$(eval $(call BuildPackage,vlmcsd))
