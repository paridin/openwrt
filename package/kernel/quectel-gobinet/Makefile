include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=quectel-gobinet
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/huangyangl/quectel_Gobinet.git
PKG_SOURCE_VERSION:=9b37e627ca1559a532fdeeab44651b96f104ca6c
PKG_MIRROR_HASH:=skip

PKG_LICENSE:=Proprietary
PKG_MAINTAINER:=HC852 Project

include $(INCLUDE_DIR)/package.mk

define KernelPackage/quectel-gobinet
  SUBMENU:=USB Support
  TITLE:=Quectel GobiNet USB WWAN driver
  DEPENDS:=+kmod-usb-net +kmod-usb-wdm +kmod-usb-serial-wwan
  FILES:=$(PKG_BUILD_DIR)/src/GobiNet.ko
  AUTOLOAD:=$(call AutoProbe,GobiNet)
  URL:=https://github.com/huangyangl/quectel_Gobinet
endef

define KernelPackage/quectel-gobinet/description
 Out-of-tree Quectel GobiNet driver.
endef

define Build/Compile
	$(KERNEL_MAKE) M="$(PKG_BUILD_DIR)/src" \
		ARCH="$(LINUX_KARCH)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		modules
endef

$(eval $(call KernelPackage,quectel-gobinet))
