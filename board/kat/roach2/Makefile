#
# (C) Copyright 2002-2006
# Wolfgang Denk, DENX Software Engineering, wd@denx.de.
#
# See file CREDITS for list of people who contributed to this
# project.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of
# the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA
#

include $(TOPDIR)/config.mk

LIB	= $(obj)lib$(BOARD).o

#TODO - cmds should be compiled if defined
COBJS-y	= $(BOARD).o sdram.o sensors.o
COBJS-$(CONFIG_CMD_R2SMAP) += cmd_r2smap.o
COBJS-$(CONFIG_CMD_R2DEBUG) += cmd_r2debug.o
COBJS-$(CONFIG_CMD_R2GPIO) += cmd_r2gpio.o
COBJS-$(CONFIG_CMD_R2SENSORS) += cmd_r2sensors.o
COBJS-$(CONFIG_CMD_R2RTC) += cmd_r2rtc.o
COBJS-$(CONFIG_CMD_R2BIT) += cmd_r2bit.o
COBJS-$(CONFIG_CMD_R2BIT) += bit/bit_qdr.o
COBJS-$(CONFIG_CMD_R2BIT) += bit/bit_tge.o
COBJS-$(CONFIG_CMD_R2BIT) += bit/bit_v6gbe.o
COBJS-$(CONFIG_CMD_R2BIT) += bit/bit_v6comm.o
COBJS-$(CONFIG_CMD_R2BIT) += bit/bit_zdok.o
COBJS-$(CONFIG_CMD_R2BIT) += bit/bit_ddr3.o
SOBJS	= init.o

COBJS   := $(COBJS-y)
SRCS	:= $(SOBJS:.o=.S) $(COBJS:.o=.c)
OBJS	:= $(addprefix $(obj),$(COBJS))
SOBJS	:= $(addprefix $(obj),$(SOBJS))

all:	$(LIB) $(SOBJS)

$(LIB):	$(OBJS)
	$(call cmd_link_o_target, $^)

clean:
	rm -f $(SOBJS) $(OBJS)

distclean:	clean
	rm -f $(LIB) core *.bak $(obj).depend

#########################################################################

# defines $(obj).depend target
include $(SRCTREE)/rules.mk

sinclude $(obj).depend

#########################################################################
