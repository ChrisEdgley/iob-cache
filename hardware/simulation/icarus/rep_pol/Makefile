#module paths
CACHE_DIR:=../../../..
INTERCON_DIR:=$(CACHE_DIR)/submodules/iob-interconnect
MEM_DIR:=$(CACHE_DIR)/submodules/iob-mem
AXI_MEM_DIR:=$(CACHE_DIR)/submodules/axi-mem
#testbench
VSRC+=$(CACHE_HW_DIR)/testbench/rep_pol_tb.v

incdir:=-I
define:=-D


#core
include $(CACHE_DIR)/hardware/hardware.mk

#additional includes
INCLUDE+=$(incdir)$(CACHE_HW_DIR)/testbench/
VHDR+=$(CACHE_HW_DIR)/testbench/rep_pol_tb.vh

#additional defines
DEFINE+=$(define)DATA_W=32 $(define)ADDR_W=32

#icarus verilog simulator
VLOG = 	iverilog -W all -g2005-sv

all: a.out
	./$< +vcd

a.out:	$(VSRC) $(VHDR)
	$(VLOG) $(INCLUDE) $(DEFINE) $(VSRC)

clean:
	@rm -f *# *~ *.vcd a.out *_tb

.PHONY: all clean
