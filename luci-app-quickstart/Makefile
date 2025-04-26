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
# Detect and process Chinese language files
define Package/$(LUCI_PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/i18n
	# Recursively search for .po files and process only zh-cn files
	find ./po -type f -name "*.po" | while read po_file; do \
		# Extract the basename of the .po file
		po_basename=$$(basename $$po_file .po); \
		# Check if the file is a zh-cn language file
		if [[ "$$po_file" =~ /zh-cn/ || "$$po_basename" =~ zh-cn ]]; then \
			# Convert .po to .lmo, ensure the target directory exists
			po2lmo $$po_file $(1)/usr/lib/lua/luci/i18n/$$po_basename.zh-cn.lmo || echo "Warning: Failed to convert $$po_file"; \
		fi; \
	done
endef
#-----------2025.04.25---以上新增中文语言包处理逻辑-----------------#

# call BuildPackage - OpenWrt buildroot signature
