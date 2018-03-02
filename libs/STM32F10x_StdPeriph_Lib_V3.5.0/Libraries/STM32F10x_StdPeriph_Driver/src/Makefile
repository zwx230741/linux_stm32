include ../../../../../Makefile.common

LIBS+=libstm32.a
CFLAGSlib+=-c
  
all: $(LIBS)

libstm32.a:
	@echo -n "Building $@ ..."
	cd $(STMLIB)/CMSIS/CM3/DeviceSupport/ST/STM32F10x/ && \
		$(CC) $(CFLAGSlib) system_stm32f10x.c
	cd $(STMLIB)/CMSIS/CM3/DeviceSupport/ST/STM32F10x/startup/arm && \
		$(CC) $(CFLAGSlib) startup.c
	cd $(STMLIB)/STM32F10x_StdPeriph_Driver/src && \
		$(CC) $(CFLAGSlib) *.c \
		-D"assert_param(expr)=((void)0)"
	$(AR) cr $(LIBDIR)/$@ \
	$(STMLIB)/CMSIS/CM3/DeviceSupport/ST/STM32F10x/system_stm32f10x.o \
	$(STMLIB)/CMSIS/CM3/DeviceSupport/ST/STM32F10x/startup/arm/startup.o \
	$(STMLIB)/STM32F10x_StdPeriph_Driver/src/*.o
	@echo "done."

.PHONY: clean
  
clean:
	rm -f $(STMLIB)/CMSIS/CM3/DeviceSupport/ST/STM32F10x/system_stm32f10x.o
	rm -f $(STMLIB)/STM32F10x_StdPeriph_Driver/src/*.o
	rm -f $(LIBDIR)/$(LIBS)
