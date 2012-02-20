all:
	mv pspnet_adhocctl.prx ../dist/kd/pspnet_adhocctl.prx

TARGET = pspnet_adhocctl

LIBRARYOBJS = \
library/calls/init.o \
library/calls/term.o \
library/calls/getstate.o \
library/calls/getadhocid.o \
library/calls/getparameter.o \
library/calls/addhandler.o \
library/calls/delhandler.o \
library/calls/scan.o \
library/calls/getscaninfo.o \
library/calls/getpeerinfo.o \
library/calls/getpeerlist.o \
library/calls/getaddrbyname.o \
library/calls/getnamebyaddr.o \
library/calls/adhocmode/create.o \
library/calls/adhocmode/connect.o \
library/calls/adhocmode/join.o \
library/calls/adhocmode/disconnect.o \
library/calls/gamemode/create.o \
library/calls/gamemode/createmin.o \
library/calls/gamemode/join.o \
library/calls/gamemode/exit.o \
library/calls/gamemode/getinfo.o \
library/calls/netconf/init.o \
library/calls/netconf/getstatus.o \
library/calls/netconf/update.o \
library/calls/netconf/shutdown.o

LIBS = -lpspwlan

OBJS = main.o ../memab/ATPRO.o $(LIBRARYOBJS)

#CFLAGS = -Os -G0 -Wall -fno-pic
CFLAGS = -O0 -G0 -Wall -fno-pic

ifeq ($(CONFIG_620), 1)
CFLAGS += -DCONFIG_620=1
endif

ifeq ($(CONFIG_63X), 1)
CFLAGS += -DCONFIG_63X=1
endif

ifeq ($(CONFIG_660), 1)
CFLAGS += -DCONFIG_660=1
endif

ifeq ($(RELEASE), 1)
CFLAGS += -DRELEASE=1
else
CFLAGS += -DDEBUG=1
endif

ifeq ($(NO_FRIEND_TIMEOUT), 1)
CFLAGS += -DNO_FRIEND_TIMEOUT=1
endif

ifeq ($(NO_FRIEND_GROUP_CHECK), 1)
CFLAGS += -DNO_FRIEND_GROUP_CHECK=1
endif

ifeq ($(PDP_DIRTY_MAGIC), 1)
CFLAGS += -DPDP_DIRTY_MAGIC=1
endif

CXXFLAGS = $(CFLAGS) -fno-exceptions -fno-rtti
ASFLAGS = $(CFLAGS)

BUILD_PRX = 1
PRX_EXPORTS = exports.exp

USE_PSPSDK_LIBC = 1

LDFLAGS = -mno-crt0 -nostartfiles

PSPSDK=$(shell psp-config --pspsdk-path)
include $(PSPSDK)/lib/build.mak