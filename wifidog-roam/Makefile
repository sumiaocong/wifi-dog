all:
	cd wifidog && ./autogen.sh --host=mips-linux  \
	--build=x86_64-linux-gnu \
	--prefix=$(shell pwd)/install \
	CC=$(CROSS_COMPILE)gcc \
	CXX=$(CROSS_COMPILE)g++ \
	LD=$(CROSS_COMPILE)ld \
	RANLIB=$(CROSS_COMPILE)ranlib \
	AR=$(CROSS_COMPILE)ar && make && make install
	
clean:
	make -C wifidog clean
	-rm -rf $(ROOTDIR)/romfs/lib/libhttpd.so*

romfs:
	$(ROMFSINST) install/bin/wifidog /bin/wifidog
	$(ROMFSINST) install/bin/wdctl /bin/wdctl
	$(ROMFSINST) install/lib/libhttpd.so.0.0.0 /lib/libhttpd.so.0.0.0
	cd $(ROOTDIR)/romfs/lib && ln -fs libhttpd.so.0.0.0 libhttpd.so.0
	cd $(ROOTDIR)/romfs/lib && ln -fs libhttpd.so.0.0.0 libhttpd.so
	$(ROMFSINST) wifidog/wifidog.conf /etc/wifidog.conf
	$(ROMFSINST) wifidog/wifidog.conf /etc/wifidog-msg.html

