include $(TOPDIR)/rules.mk

PKG_NAME:=logtrigger
PKG_VERSION:=1.1.0
PKG_RELEASE:=4

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/amoncusir/logtrigger.git
PKG_SOURCE_DATE:=2023-10-22
PKG_SOURCE_VERSION:=bdedf6cdf1ac3a5ad5efd3cadc280e17ae04ee7c
PKG_MIRROR_HASH:=38bde73e357ed71b431e8783706302779aacc3a0dff45fdc778b41a319ca4aa4

PKG_MAINTAINER:=Aran Moncusi Ramirez <aran@digitalpoet.info>
PKG_LICENSE:=GPL-3.0-or-later

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/logtrigger
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=logtrigger
	DEPENDS:=+libstdcpp +libubus +libubox +ubox
endef

define Package/logtrigger/description
	Execute scripts triggered by log
endef

define Package/logtrigger/conffiles
/etc/config/logtrigger
endef

define Build/logtrigger/prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) $(SOURCE_DIR)/* $(PKG_BUILD_DIR)
	$(Build/Patch)
endef

define Package/logtrigger/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/logtrigger $(1)/usr/sbin/

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/logtrigger.conf $(1)/etc/config/logtrigger

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/logtrigger.init $(1)/etc/init.d/logtrigger

	$(INSTALL_DIR) $(1)/usr/share/logtrigger/
	$(INSTALL_BIN) ./files/logs.sh $(1)/usr/share/logtrigger/logs.sh
endef

$(eval $(call BuildPackage,logtrigger))