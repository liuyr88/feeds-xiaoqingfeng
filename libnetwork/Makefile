include $(TOPDIR)/rules.mk

PKG_NAME:=libnetwork
PKG_RELEASE:=2
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://$(GO_PKG)
PKG_SOURCE_VERSION:=026aabaa659832804b01754aaadd2c0f420c68b6
PKG_SOURCE_DATE:=2020-06-17
PKG_MIRROR_HASH:=4ec8d3a7a99478dae9aef9f8337c14b91750164351963f9a6ed2288588d080e3

PKG_MAINTAINER:=Gerard Ryan <G.M0N3Y.2503@gmail.com>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1

GO_PKG:=github.com/docker/libnetwork
GO_PKG_BUILD_PKG:= \
  $(GO_PKG)/cmd/proxy \
  $(GO_PKG)/cmd/dnet

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/libnetwork
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=networking for containers
  URL:=https://github.com/docker/libnetwork
  DEPENDS:=$(GO_ARCH_DEPENDS) @(aarch64||arm||x86_64)
endef

define Package/libnetwork/description
Libnetwork provides a native Go implementation for connecting containers.
The goal of libnetwork is to deliver a robust Container Network Model that provides a consistent programming interface and the required network abstractions for applications.
endef

define Package/libnetwork/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/dnet $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/proxy $(1)/usr/bin/docker-proxy
endef

$(eval $(call GoBinPackage,libnetwork))
$(eval $(call BuildPackage,libnetwork))
