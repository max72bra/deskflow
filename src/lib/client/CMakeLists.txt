# SPDX-FileCopyrightText: (C) 2024, 2026 Chris Rizzitello <sithlord48@gmail.com>
# SPDX-FileCopyrightText: (C) 2012 - 2024 Symless Ltd
# SPDX-FileCopyrightText: (C) 2009 - 2012 Nick Bolton
# SPDX-License-Identifier: MIT

add_library(client STATIC
  Client.cpp
  Client.h
  ServerProxy.cpp
  ServerProxy.h
  ServerProxy1_7.cpp
  ServerProxy1_7.h
  ServerProxy1_8.cpp
  ServerProxy1_8.h
)

target_link_libraries(client PUBLIC common)

# Km0: the version reported to Km0 (kMsgDVersion), the release tag without "v" in CI (e.g. 1.27.0-km0.3);
# local builds report none
if(PACKAGE_VERSION_LABEL)
  target_compile_definitions(client PRIVATE KM0_VERSION="${PACKAGE_VERSION_LABEL}")
endif()
