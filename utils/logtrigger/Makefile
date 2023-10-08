include $(TOPDIR)/rules.mk

PKG_NAME:=logtrigger
PKG_VERSION:=1.0.0
PKG_RELEASE:=0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/amoncusir/logtrigger.git
PKG_SOURCE_DATE:=2023-10-08
PKG_SOURCE_VERSION:=7623e718f1e704df622d3f852428e292ad7609db
PKG_MIRROR_HASH:=57a0e7333b65b46c7be4d2d8137affac0163ec97b2debfb966d7df56ebca2f8c

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