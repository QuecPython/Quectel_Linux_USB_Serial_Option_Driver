KERNELDIR := /lib/modules/$(shell uname -r)/build
PWD       := $(shell pwd)

obj-m+=./drivers/usb/serial/option.o

modules: clean
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules

install: modules
	cp $(PWD)/drivers/usb/serial/*.ko /lib/modules/$(shell uname -r)/kernel/drivers/usb/serial/
	depmod

clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) clean
