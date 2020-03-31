include $(TOPDIR)/rules.mk

PKG_NAME:=freedns-go
PKG_VERSION:=2020.1.16
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/tuna/freedns-go/archive/
PKG_HASH:=111891bb60d9faf00eac82efcaac72a5e6c40a3893b2445d7276e91ccc8b2837

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Xiang Liu <kookxiang@gmail.com>

PKG_BUILD_DEPENDS:=golang/host python3/host

GO_PKG:=github.com/tuna/freedns-go
GO_PKG_LDFLAGS:=-s -w
GO_PKG_LDFLAGS_X:=main.version=$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Build/Prepare
	$(Build/Prepare/Default)
	pip3 install requests
	cd $(PKG_BUILD_DIR)/chinaip; python3 ./update_db.py
endef

define Package/freedns-go
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=IP Addresses and Names
	TITLE:=Optimized DNS Server for Chinese users.
	URL:=https://github.com/tuna/freedns-go
	DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/freedns-go/install
	$(call GoPackage/Package/Install/Bin,$(1))
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./init.d/* $(1)/etc/init.d/
endef

define Package/freedns-go/description
	Optimized DNS Server for Chinese users.
	https://github.com/tuna/freedns-go
endef

$(eval $(call GoBinPackage,freedns-go))
$(eval $(call BuildPackage,freedns-go))
