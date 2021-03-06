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
# Copyright (c) 2018, Oracle and/or its affiliates. All rights reserved.
#

BUILD_BITS =            32_and_64
include ../../../../make-rules/shared-macros.mk

COMPONENT_NAME=		freetype
COMPONENT_VERSION=	2.8
COMPONENT_PROJECT_URL=	http://freetype.org/
COMPONENT_ARCHIVE_URL=	http://download.savannah.gnu.org/releases/freetype/$(COMPONENT_ARCHIVE)
COMPONENT_ARCHIVE_HASH= \
	sha256:a3c603ed84c3c2495f9c9331fe6bba3bb0ee65e06ec331e0a0fb52158291b40b
COMPONENT_BUGDB=        x11/font
COMPONENT_ANITYA_ID=	854
TPNO=			35528

TEST_TARGET = $(NO_TESTS)

FIX_PC_FILES=builds/unix/freetype2.in

include $(WS_MAKE_RULES)/x11-component.mk

CONFIGURE_OPTIONS += --enable-biarch-config
CONFIGURE_OPTIONS += --with-zlib
CONFIGURE_OPTIONS += --with-bzip2
CONFIGURE_OPTIONS += --with-png
CONFIGURE_OPTIONS += --with-pic
CONFIGURE_OPTIONS += --without-harfbuzz

LDFLAGS += -lc

REQUIRED_PACKAGES += compress/bzip2
REQUIRED_PACKAGES += image/library/libpng14
REQUIRED_PACKAGES += library/zlib
