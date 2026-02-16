include $(TOPDIR)/rules.mk

PKG_NAME:=quectel-cm
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/kmilo17pet/quectel-cm.git
PKG_SOURCE_VERSION:=2c623ffc8a1a8a7054b695956eb343e37b04727b
PKG_MIRROR_HASH:=skip

PKG_LICENSE:=Proprietary
PKG_LICENSE_FILES:=NOTICE
PKG_MAINTAINER:=HC852 Project

include $(INCLUDE_DIR)/package.mk

define Package/quectel-cm
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=WWAN
  TITLE:=Quectel Connect Manager
  DEPENDS:=+kmod-usb-net-qmi-wwan +kmod-usb-wdm +kmod-usb-serial-option
  URL:=https://github.com/kmilo17pet/quectel-cm
endef

define Package/quectel-cm/description
 Quectel Connect Manager userspace dialer for QMI/MBIM/GobiNet based modems.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		CFLAGS="$(TARGET_CFLAGS)" \
		release
endef

define Package/quectel-cm/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/quectel-CM $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/quectel-qmi-proxy $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/quectel-mbim-proxy $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,quectel-cm))
