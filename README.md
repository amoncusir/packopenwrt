# Custom Package source for OpenWRT #

## Add to OpenWRT

1. Clone the Openwrt git in your system
2. Edit `feeds.conf` file and add: `src-git-full digitalpoet https://github.com/amoncusir/packopenwrt.git`
3. Run in the openwrt project: `./scripts/feeds updata -a && ./scripts/feeds install -a`
4. Enable build with `make menuconfig` in Utilities menu
5. Build all `make` or the specific target like `make package/feeds/digitalpoet/logtrigger/compile`
