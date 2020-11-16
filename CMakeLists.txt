#
# file: CMakeLists.txt
#
# This is the main CMakeLists.txt for azure-sdk-for-c integration with distortos
#
# author: Copyright (C) 2020 Kamil Szczygiel http://www.distortec.com http://www.freddiechopin.info
#
# This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. If a copy of the MPL was not
# distributed with this file, You can obtain one at http://mozilla.org/MPL/2.0/.
#

cmake_minimum_required(VERSION 3.10)
project(azure-sdk-for-c-integration)

if(NOT DEFINED AZURE_SDK_FOR_C_DIRECTORY)
	message(SEND_ERROR "Variable with path to azure-sdk-for-c directory - AZURE_SDK_FOR_C_DIRECTORY - is not defined")
endif()
if(NOT IS_DIRECTORY "${AZURE_SDK_FOR_C_DIRECTORY}")
	message(SEND_ERROR "Path to azure-sdk-for-c directory - AZURE_SDK_FOR_C_DIRECTORY = ${AZURE_SDK_FOR_C_DIRECTORY} - "
			"is not valid")
endif()
if(NOT EXISTS "${AZURE_SDK_FOR_C_DIRECTORY}/CMakeLists.txt")
	message(SEND_ERROR "Path to azure-sdk-for-c directory - AZURE_SDK_FOR_C_DIRECTORY = ${AZURE_SDK_FOR_C_DIRECTORY} - "
			"does not contain CMakeLists.txt")
endif()

add_subdirectory("${AZURE_SDK_FOR_C_DIRECTORY}" azure-sdk-for-c EXCLUDE_FROM_ALL)

distortosAppendToSavedConfiguration(LOGGING)
distortosAppendToSavedConfiguration(PRECONDITIONS)
distortosAppendToSavedConfiguration(TRANSPORT_CURL)
distortosAppendToSavedConfiguration(TRANSPORT_PAHO)
distortosAppendToSavedConfiguration(UNIT_TESTING)
distortosAppendToSavedConfiguration(UNIT_TESTING_MOCKS)
distortosAppendToSavedConfiguration(WARNINGS_AS_ERRORS)
