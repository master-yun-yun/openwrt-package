# Copyright (C) 2016 Openwrt.org
#
# This is free software, licensed under the Apache License, Version 2.0 .
#

include $(TOPDIR)/rules.mk

LUCI_TITLE:=LuCI support for quickstart 
LUCI_DEPENDS:=+quickstart +luci-app-store
LUCI_PKGARCH:=all

PKG_VERSION:=0.8.17-1
# PKG_RELEASE MUST be empty for luci.mk
PKG_RELEASE:=

LUCI_MINIFY_CSS:=0
LUCI_MINIFY_JS:=0

include $(TOPDIR)/feeds/luci/luci.mk

#-----------2025.04.25---以下新增中文语言包处理逻辑-----------------#
# Ensure Chinese language file (zh-cn) is included
define Package/$(LUCI_PKG_NAME)/install
	$(LUCI_INSTALL_DIR) $(1)/usr/lib/lua/luci/i18n
	po2lmo ./po/zh-cn/$(LUCI_PKG_NAME).po $(1)/usr/lib/lua/luci/i18n/$(LUCI_PKG_NAME).zh-cn.lmo
endef
#-----------2025.04.25---以上新增中文语言包处理逻辑-----------------#

# call BuildPackage - OpenWrt buildroot signature
