#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2012, 2017, Oracle and/or its affiliates. All rights reserved.
#
BUILD_BITS= 64_and_32
include ../../make-rules/shared-macros.mk

COMPONENT_NAME=		ncurses
COMPONENT_VERSION=	6.0-20170708
IPS_COMPONENT_VERSION=	6.0.0.20170708
COMPONENT_PROJECT_URL=	http://invisible-mirror.net/archives/ncurses/current/
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tgz
COMPONENT_ARCHIVE_HASH= \
    sha256:92f7024b9fabd0cc58fb5c25bbc6b64035750a8fb980c65b34032ec8f94209a4
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/$(COMPONENT_ARCHIVE)
COMPONENT_BUGDB=	library/ncurses
COMPONENT_ANITYA_ID=	2057

TPNO=			36657

include $(WS_MAKE_RULES)/common.mk

# Needed to make "gmake test" work.
COMPONENT_PRE_CONFIGURE_ACTION += \
	($(CLONEY) $(SOURCE_DIR) $(@D))

CONFIGURE_PREFIX =	/usr/gnu

# Fix 64-bit linking via compiler.
LDFLAGS += $(CC_BITS)

# Choose a standard in case the default changes.
CXXFLAGS += -std=sun03

CONFIGURE_OPTIONS +=	--with-shared
CONFIGURE_OPTIONS +=	--with-abi-version=5
CONFIGURE_OPTIONS +=	--with-normal
CONFIGURE_OPTIONS +=	--enable-rpath
CONFIGURE_OPTIONS +=	--enable-widec
CONFIGURE_OPTIONS +=	--enable-symlinks
CONFIGURE_OPTIONS +=	--includedir=$(USRINCDIR)/ncurses
CONFIGURE_OPTIONS +=	--with-default-terminfo-dir=$(GNUSHARE)/terminfo

# We only deliver 64-bit binaries and in /usr/bin.
COMPONENT_POST_INSTALL_ACTION.32 += \
	$(GSED) -i -e 's|$(GNUBIN)/i86|$(GNUBIN)|' \
		$(PROTOGNUBIN)/$(MACH32)/ncursesw5-config;

# There is no master test file because tests are interactive and not
# tied to the build.
COMPONENT_TEST_DIR =		$(BUILD_DIR)/$(MACH$(BITS))/test
COMPONENT_TEST_TARGETS =

$(SKIP_TEST_AT_TOP_LEVEL)

REQUIRED_PACKAGES += shell/bash
