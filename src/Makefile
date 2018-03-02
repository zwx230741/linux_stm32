include ../Makefile.common

LIBS+=app.a
CFLAGSlib+=-c
  
all: $(LIBS)
  
app.a:
	@echo -n "Building $@ ..."
	$(CC) $(CFLAGSlib) *.c
	$(AR) cr $@ *.o
	@echo "done."

.PHONY: clean
  
clean:
	rm -f *.o
	rm -f $(LIBS)
