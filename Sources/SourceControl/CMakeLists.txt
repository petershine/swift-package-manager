# This source file is part of the Swift open source project
#
# Copyright (c) 2014 - 2019 Apple Inc. and the Swift project authors
# Licensed under Apache License v2.0 with Runtime Library Exception
#
# See http://swift.org/LICENSE.txt for license information
# See http://swift.org/CONTRIBUTORS.txt for Swift project authors

add_library(SourceControl
  GitRepository.swift
  Repository.swift
  RepositoryManager.swift)
target_link_libraries(SourceControl PUBLIC
  Basics
  PackageModel
  TSCBasic
  TSCUtility
  Basics)

# NOTE(compnerd) workaround for CMake not setting up include flags yet
set_target_properties(SourceControl PROPERTIES
  INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_Swift_MODULE_DIRECTORY})

install(TARGETS SourceControl
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin)
set_property(GLOBAL APPEND PROPERTY SwiftPM_EXPORTS SourceControl)
