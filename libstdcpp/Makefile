#
# Copyright (C) 2007-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
PKG_NAME:=libstdcpp
PKG_RELEASE:=1
PKG_VERSION:=6.0

PKG_LICENSE:=GPL-3.0-with-GCC-exception

include $(INCLUDE_DIR)/package.mk

define Package/libstdcpp
  SECTION:=libs
  CATEGORY:=Base system
  URL:=http://gcc.gnu.org/
  NAME:=libstdc++
  TITLE:=GNU Standard C++ Library v3
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
endef

define Build/Compile
	# nothing to do
endef

ifeq ($(CONFIG_TOOLCHAIN_LIBC_GLIBC),y)
define Package/libstdcpp/install
	$(INSTALL_DIR) $(1)/lib
	find $(BUILD_DIR_TOOLCHAIN)/tools-*/*-gnu/sysroot/lib -name libstdc++.so* -exec cp -r {} $(1)/lib/ \;
	rm -f $(1)/lib/libstdc++*.py
endef
else
define Package/libstdcpp/install
	$(INSTALL_DIR) $(1)/lib
	$(CP) $(BUILD_DIR_TOOLCHAIN)/sysroot-*/lib/libstdc++.so* $(1)/lib/
	rm -f $(1)/lib/libstdc++*.py
endef
endif

$(eval $(call BuildPackage,libstdcpp))
