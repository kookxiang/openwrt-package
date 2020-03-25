include $(TOPDIR)/rules.mk

PKG_NAME:=dnsproxy
PKG_VERSION:=0.24.0
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/AdguardTeam/dnsproxy/archive/
PKG_HASH:=6b12caa51e797aa5bb8da219dd4db831ca680e8811de92859250b71d0bbf282a

PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Xiang Liu <kookxiang@gmail.com>

PKG_BUILD_DEPENDS:=golang/host

GO_PKG:=github.com/AdguardTeam/dnsproxy
GO_PKG_LDFLAGS:=-s -w
GO_PKG_LDFLAGS_X:=main.version=$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/dnsproxy
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=IP Addresses and Names
	TITLE:=Simple DNS proxy with DoH, DoT, and DNSCrypt support.
	URL:=https://github.com/AdguardTeam/dnsproxy
	DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/dnsproxy/install
	$(call GoPackage/Package/Install/Bin,$(1))

	$(INSTALL_DIR) $(1)/usr/bin
endef

define Package/dnsproxy/description
	Simple DNS proxy with DoH, DoT, and DNSCrypt support.
	https://github.com/AdguardTeam/dnsproxy
endef

$(eval $(call GoBinPackage,dnsproxy))
$(eval $(call BuildPackage,dnsproxy))
