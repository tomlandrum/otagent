#[[
// clang-format off
]]#
# Copyright (c) 2018 The Open-Transactions developers
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

set(name unittests-otagent)

set(cxx-sources
  main.cpp
  OTTestEnvironment.cpp
)

include_directories(
  ${PROJECT_SOURCE_DIR}/src
  ${PROJECT_SOURCE_DIR}/tests
  ${GTEST_INCLUDE_DIRS}
)

add_executable(${name} ${cxx-sources})
add_dependencies(unittests-otagent otagent)
target_link_libraries(${name} opentxs ${PROTOBUF_LITE_LIBRARIES} ${GTEST_BOTH_LIBRARIES} pthread)
set_target_properties(${name} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/tests)
add_test(${name} ${PROJECT_BINARY_DIR}/tests/${name} --gtest_output=xml:gtestresults.xml)

#[[
// clang-format on
]]#
