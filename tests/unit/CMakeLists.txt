# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

add_definitions(-DUNIT_TEST)
add_definitions(-DMVPN_ADJUST)

get_filename_component(MVPN_SOURCE_DIR ${CMAKE_SOURCE_DIR}/src ABSOLUTE)

include_directories(${CMAKE_CURRENT_BINARY_DIR})
include_directories(${MVPN_SOURCE_DIR})
include_directories(${MVPN_SOURCE_DIR}/composer)
include_directories(${MVPN_SOURCE_DIR}/hacl-star)
include_directories(${MVPN_SOURCE_DIR}/hacl-star/kremlin)
include_directories(${MVPN_SOURCE_DIR}/hacl-star/kremlin/minimal)
include_directories(${CMAKE_SOURCE_DIR}/tests/unit)

qt_add_executable(unit_tests EXCLUDE_FROM_ALL)
set_target_properties(unit_tests PROPERTIES FOLDER "Tests")
add_dependencies(build_tests unit_tests)

target_link_libraries(unit_tests PRIVATE
    Qt6::Core
    Qt6::Xml
    Qt6::Network
    Qt6::Test
    Qt6::WebSockets
    Qt6::Widgets
    Qt6::Gui
    Qt6::Qml
    Qt6::Quick
)

target_link_libraries(unit_tests PRIVATE glean lottie nebula translations)

# VPN Client source files
target_sources(unit_tests PRIVATE
    ${MVPN_SOURCE_DIR}/addons/addon.cpp
    ${MVPN_SOURCE_DIR}/addons/addon.h
    ${MVPN_SOURCE_DIR}/addons/addonapi.cpp
    ${MVPN_SOURCE_DIR}/addons/addonapi.h
    ${MVPN_SOURCE_DIR}/addons/addonguide.cpp
    ${MVPN_SOURCE_DIR}/addons/addonguide.cpp
    ${MVPN_SOURCE_DIR}/addons/addonguide.h
    ${MVPN_SOURCE_DIR}/addons/addoni18n.cpp
    ${MVPN_SOURCE_DIR}/addons/addoni18n.h
    ${MVPN_SOURCE_DIR}/addons/addonmessage.cpp
    ${MVPN_SOURCE_DIR}/addons/addonmessage.h
    ${MVPN_SOURCE_DIR}/addons/addonproperty.cpp
    ${MVPN_SOURCE_DIR}/addons/addonproperty.h
    ${MVPN_SOURCE_DIR}/addons/addonpropertylist.cpp
    ${MVPN_SOURCE_DIR}/addons/addonpropertylist.h
    ${MVPN_SOURCE_DIR}/addons/addontutorial.cpp
    ${MVPN_SOURCE_DIR}/addons/addontutorial.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcher.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcher.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcherfeaturesenabled.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcherfeaturesenabled.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchergroup.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchergroup.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcherjavascript.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcherjavascript.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcherlocales.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatcherlocales.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchertimeend.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchertimeend.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchertimestart.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchertimestart.h
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchertriggertimesecs.cpp
    ${MVPN_SOURCE_DIR}/addons/conditionwatchers/addonconditionwatchertriggertimesecs.h
    ${MVPN_SOURCE_DIR}/addons/manager/addondirectory.cpp
    ${MVPN_SOURCE_DIR}/addons/manager/addondirectory.h
    ${MVPN_SOURCE_DIR}/addons/manager/addonindex.cpp
    ${MVPN_SOURCE_DIR}/addons/manager/addonindex.h
    ${MVPN_SOURCE_DIR}/addons/manager/addonmanager.cpp
    ${MVPN_SOURCE_DIR}/addons/manager/addonmanager.h
    ${MVPN_SOURCE_DIR}/adjust/adjustfiltering.cpp
    ${MVPN_SOURCE_DIR}/adjust/adjustfiltering.h
    ${MVPN_SOURCE_DIR}/adjust/adjustproxypackagehandler.cpp
    ${MVPN_SOURCE_DIR}/adjust/adjustproxypackagehandler.h
    ${MVPN_SOURCE_DIR}/captiveportal/captiveportal.cpp
    ${MVPN_SOURCE_DIR}/captiveportal/captiveportal.h
    ${MVPN_SOURCE_DIR}/collator.cpp
    ${MVPN_SOURCE_DIR}/collator.h
    ${MVPN_SOURCE_DIR}/command.cpp
    ${MVPN_SOURCE_DIR}/command.h
    ${MVPN_SOURCE_DIR}/commandlineparser.cpp
    ${MVPN_SOURCE_DIR}/commandlineparser.h
    ${MVPN_SOURCE_DIR}/composer/composer.cpp
    ${MVPN_SOURCE_DIR}/composer/composer.h
    ${MVPN_SOURCE_DIR}/composer/composerblock.cpp
    ${MVPN_SOURCE_DIR}/composer/composerblock.h
    ${MVPN_SOURCE_DIR}/composer/composerblockbutton.cpp
    ${MVPN_SOURCE_DIR}/composer/composerblockbutton.h
    ${MVPN_SOURCE_DIR}/composer/composerblockorderedlist.cpp
    ${MVPN_SOURCE_DIR}/composer/composerblockorderedlist.h
    ${MVPN_SOURCE_DIR}/composer/composerblocktext.cpp
    ${MVPN_SOURCE_DIR}/composer/composerblocktext.h
    ${MVPN_SOURCE_DIR}/composer/composerblocktitle.cpp
    ${MVPN_SOURCE_DIR}/composer/composerblocktitle.h
    ${MVPN_SOURCE_DIR}/composer/composerblockunorderedlist.cpp
    ${MVPN_SOURCE_DIR}/composer/composerblockunorderedlist.h
    ${MVPN_SOURCE_DIR}/constants.cpp
    ${MVPN_SOURCE_DIR}/constants.h
    ${MVPN_SOURCE_DIR}/controller.h
    ${MVPN_SOURCE_DIR}/cryptosettings.cpp
    ${MVPN_SOURCE_DIR}/cryptosettings.h
    ${MVPN_SOURCE_DIR}/curve25519.cpp
    ${MVPN_SOURCE_DIR}/curve25519.h
    ${MVPN_SOURCE_DIR}/dnspingsender.cpp
    ${MVPN_SOURCE_DIR}/dnspingsender.h
    ${MVPN_SOURCE_DIR}/env.h
    ${MVPN_SOURCE_DIR}/errorhandler.cpp
    ${MVPN_SOURCE_DIR}/errorhandler.h
    ${MVPN_SOURCE_DIR}/externalophandler.cpp
    ${MVPN_SOURCE_DIR}/externalophandler.h
    ${MVPN_SOURCE_DIR}/frontend/navigator.cpp
    ${MVPN_SOURCE_DIR}/frontend/navigator.h
    ${MVPN_SOURCE_DIR}/frontend/navigatorreloader.cpp
    ${MVPN_SOURCE_DIR}/frontend/navigatorreloader.h
    ${MVPN_SOURCE_DIR}/hacl-star/Hacl_Chacha20.c
    ${MVPN_SOURCE_DIR}/hacl-star/Hacl_Chacha20Poly1305_32.c
    ${MVPN_SOURCE_DIR}/hacl-star/Hacl_Curve25519_51.c
    ${MVPN_SOURCE_DIR}/hacl-star/Hacl_Poly1305_32.c
    ${MVPN_SOURCE_DIR}/inspector/inspectorhandler.h
    ${MVPN_SOURCE_DIR}/inspector/inspectorutils.cpp
    ${MVPN_SOURCE_DIR}/inspector/inspectorutils.h
    ${MVPN_SOURCE_DIR}/ipaddress.cpp
    ${MVPN_SOURCE_DIR}/ipaddress.h
    ${MVPN_SOURCE_DIR}/ipaddresslookup.cpp
    ${MVPN_SOURCE_DIR}/ipaddresslookup.h
    ${MVPN_SOURCE_DIR}/itempicker.cpp
    ${MVPN_SOURCE_DIR}/itempicker.h
    ${MVPN_SOURCE_DIR}/leakdetector.cpp
    ${MVPN_SOURCE_DIR}/leakdetector.h
    ${MVPN_SOURCE_DIR}/localizer.cpp
    ${MVPN_SOURCE_DIR}/localizer.h
    ${MVPN_SOURCE_DIR}/logger.cpp
    ${MVPN_SOURCE_DIR}/logger.h
    ${MVPN_SOURCE_DIR}/loghandler.cpp
    ${MVPN_SOURCE_DIR}/loghandler.h
    ${MVPN_SOURCE_DIR}/models/device.cpp
    ${MVPN_SOURCE_DIR}/models/device.h
    ${MVPN_SOURCE_DIR}/models/devicemodel.cpp
    ${MVPN_SOURCE_DIR}/models/devicemodel.h
    ${MVPN_SOURCE_DIR}/models/feature.cpp
    ${MVPN_SOURCE_DIR}/models/feature.h
    ${MVPN_SOURCE_DIR}/models/featuremodel.cpp
    ${MVPN_SOURCE_DIR}/models/featuremodel.h
    ${MVPN_SOURCE_DIR}/models/feedbackcategorymodel.cpp
    ${MVPN_SOURCE_DIR}/models/feedbackcategorymodel.h
    ${MVPN_SOURCE_DIR}/models/keys.cpp
    ${MVPN_SOURCE_DIR}/models/keys.h
    ${MVPN_SOURCE_DIR}/models/licensemodel.cpp
    ${MVPN_SOURCE_DIR}/models/licensemodel.h
    ${MVPN_SOURCE_DIR}/models/server.cpp
    ${MVPN_SOURCE_DIR}/models/server.h
    ${MVPN_SOURCE_DIR}/models/servercity.cpp
    ${MVPN_SOURCE_DIR}/models/servercity.h
    ${MVPN_SOURCE_DIR}/models/servercountry.cpp
    ${MVPN_SOURCE_DIR}/models/servercountry.h
    ${MVPN_SOURCE_DIR}/models/servercountrymodel.cpp
    ${MVPN_SOURCE_DIR}/models/servercountrymodel.h
    ${MVPN_SOURCE_DIR}/models/serverdata.cpp
    ${MVPN_SOURCE_DIR}/models/serverdata.h
    ${MVPN_SOURCE_DIR}/models/subscriptiondata.cpp
    ${MVPN_SOURCE_DIR}/models/subscriptiondata.h
    ${MVPN_SOURCE_DIR}/models/supportcategorymodel.cpp
    ${MVPN_SOURCE_DIR}/models/supportcategorymodel.h
    ${MVPN_SOURCE_DIR}/models/user.cpp
    ${MVPN_SOURCE_DIR}/models/user.h
    ${MVPN_SOURCE_DIR}/mozillavpn.h
    ${MVPN_SOURCE_DIR}/networkmanager.cpp
    ${MVPN_SOURCE_DIR}/networkmanager.h
    ${MVPN_SOURCE_DIR}/networkrequest.h
    ${MVPN_SOURCE_DIR}/networkwatcher.cpp
    ${MVPN_SOURCE_DIR}/networkwatcher.h
    ${MVPN_SOURCE_DIR}/networkwatcherimpl.h
    ${MVPN_SOURCE_DIR}/notificationhandler.cpp
    ${MVPN_SOURCE_DIR}/notificationhandler.h
    ${MVPN_SOURCE_DIR}/pinghelper.cpp
    ${MVPN_SOURCE_DIR}/pinghelper.h
    ${MVPN_SOURCE_DIR}/pingsender.h
    ${MVPN_SOURCE_DIR}/pingsenderfactory.cpp
    ${MVPN_SOURCE_DIR}/pingsenderfactory.h
    ${MVPN_SOURCE_DIR}/platforms/dummy/dummycryptosettings.cpp
    ${MVPN_SOURCE_DIR}/platforms/dummy/dummynetworkwatcher.cpp
    ${MVPN_SOURCE_DIR}/platforms/dummy/dummynetworkwatcher.h
    ${MVPN_SOURCE_DIR}/platforms/dummy/dummypingsender.cpp
    ${MVPN_SOURCE_DIR}/platforms/dummy/dummypingsender.h
    ${MVPN_SOURCE_DIR}/qmlengineholder.cpp
    ${MVPN_SOURCE_DIR}/qmlengineholder.h
    ${MVPN_SOURCE_DIR}/releasemonitor.cpp
    ${MVPN_SOURCE_DIR}/releasemonitor.h
    ${MVPN_SOURCE_DIR}/rfc/rfc1918.cpp
    ${MVPN_SOURCE_DIR}/rfc/rfc1918.h
    ${MVPN_SOURCE_DIR}/rfc/rfc4193.cpp
    ${MVPN_SOURCE_DIR}/rfc/rfc4193.h
    ${MVPN_SOURCE_DIR}/rfc/rfc4291.cpp
    ${MVPN_SOURCE_DIR}/rfc/rfc4291.h
    ${MVPN_SOURCE_DIR}/rfc/rfc5735.cpp
    ${MVPN_SOURCE_DIR}/rfc/rfc5735.h
    ${MVPN_SOURCE_DIR}/serveri18n.cpp
    ${MVPN_SOURCE_DIR}/serveri18n.h
    ${MVPN_SOURCE_DIR}/settingsholder.cpp
    ${MVPN_SOURCE_DIR}/settingsholder.h
    ${MVPN_SOURCE_DIR}/signature.cpp
    ${MVPN_SOURCE_DIR}/signature.h
    ${MVPN_SOURCE_DIR}/simplenetworkmanager.cpp
    ${MVPN_SOURCE_DIR}/simplenetworkmanager.h
    ${MVPN_SOURCE_DIR}/statusicon.cpp
    ${MVPN_SOURCE_DIR}/statusicon.h
    ${MVPN_SOURCE_DIR}/systemtraynotificationhandler.h
    ${MVPN_SOURCE_DIR}/task.h
    ${MVPN_SOURCE_DIR}/tasks/account/taskaccount.cpp
    ${MVPN_SOURCE_DIR}/tasks/account/taskaccount.h
    ${MVPN_SOURCE_DIR}/tasks/adddevice/taskadddevice.cpp
    ${MVPN_SOURCE_DIR}/tasks/adddevice/taskadddevice.h
    ${MVPN_SOURCE_DIR}/tasks/addon/taskaddon.cpp
    ${MVPN_SOURCE_DIR}/tasks/addon/taskaddon.h
    ${MVPN_SOURCE_DIR}/tasks/addonindex/taskaddonindex.cpp
    ${MVPN_SOURCE_DIR}/tasks/addonindex/taskaddonindex.h
    ${MVPN_SOURCE_DIR}/tasks/function/taskfunction.cpp
    ${MVPN_SOURCE_DIR}/tasks/function/taskfunction.h
    ${MVPN_SOURCE_DIR}/tasks/group/taskgroup.cpp
    ${MVPN_SOURCE_DIR}/tasks/group/taskgroup.h
    ${MVPN_SOURCE_DIR}/tasks/ipfinder/taskipfinder.cpp
    ${MVPN_SOURCE_DIR}/tasks/ipfinder/taskipfinder.h
    ${MVPN_SOURCE_DIR}/tasks/release/taskrelease.cpp
    ${MVPN_SOURCE_DIR}/tasks/release/taskrelease.h
    ${MVPN_SOURCE_DIR}/tasks/servers/taskservers.cpp
    ${MVPN_SOURCE_DIR}/tasks/servers/taskservers.h
    ${MVPN_SOURCE_DIR}/taskscheduler.cpp
    ${MVPN_SOURCE_DIR}/taskscheduler.h
    ${MVPN_SOURCE_DIR}/temporarydir.cpp
    ${MVPN_SOURCE_DIR}/temporarydir.h
    ${MVPN_SOURCE_DIR}/theme.cpp
    ${MVPN_SOURCE_DIR}/theme.h
    ${MVPN_SOURCE_DIR}/tutorial/tutorial.cpp
    ${MVPN_SOURCE_DIR}/tutorial/tutorial.h
    ${MVPN_SOURCE_DIR}/tutorial/tutorialstep.cpp
    ${MVPN_SOURCE_DIR}/tutorial/tutorialstep.h
    ${MVPN_SOURCE_DIR}/tutorial/tutorialstepbefore.cpp
    ${MVPN_SOURCE_DIR}/tutorial/tutorialstepbefore.h
    ${MVPN_SOURCE_DIR}/tutorial/tutorialstepnext.cpp
    ${MVPN_SOURCE_DIR}/tutorial/tutorialstepnext.h
    ${MVPN_SOURCE_DIR}/update/updater.cpp
    ${MVPN_SOURCE_DIR}/update/updater.h
    ${MVPN_SOURCE_DIR}/update/versionapi.cpp
    ${MVPN_SOURCE_DIR}/update/versionapi.h
    ${MVPN_SOURCE_DIR}/update/webupdater.cpp
    ${MVPN_SOURCE_DIR}/update/webupdater.h
    ${MVPN_SOURCE_DIR}/urlopener.cpp
    ${MVPN_SOURCE_DIR}/urlopener.h
    ${MVPN_SOURCE_DIR}/websocket/exponentialbackoffstrategy.cpp
    ${MVPN_SOURCE_DIR}/websocket/exponentialbackoffstrategy.h
    ${MVPN_SOURCE_DIR}/websocket/pushmessage.cpp
    ${MVPN_SOURCE_DIR}/websocket/pushmessage.h
    ${MVPN_SOURCE_DIR}/websocket/websockethandler.cpp
    ${MVPN_SOURCE_DIR}/websocket/websockethandler.h
)

# VPN Client UI resources
target_sources(unit_tests PRIVATE
    ${MVPN_SOURCE_DIR}/ui/license.qrc
    ${MVPN_SOURCE_DIR}/resources/public_keys/public_keys.qrc
)

# Unit test source files
target_sources(unit_tests PRIVATE
    main.cpp
    moccontroller.cpp
    mocinspectorhandler.cpp
    mocmozillavpn.cpp
    mocnetworkrequest.cpp
    mocsystemtraynotificationhandler.cpp
    helper.h
    testaddon.cpp
    testaddon.h
    testaddonapi.cpp
    testaddonapi.h
    testaddonindex.cpp
    testaddonindex.h
    testadjust.cpp
    testadjust.h
    testcommandlineparser.cpp
    testcommandlineparser.h
    testcomposer.cpp
    testcomposer.h
    testfeature.cpp
    testfeature.h
    testipaddress.cpp
    testipaddress.h
    testipaddresslookup.cpp
    testipaddresslookup.h
    testipfinder.cpp
    testipfinder.h
    testlicense.cpp
    testlicense.h
    testlocalizer.cpp
    testlocalizer.h
    testlogger.cpp
    testlogger.h
    testmodels.cpp
    testmodels.h
    testmozillavpnh.cpp
    testmozillavpnh.h
    testnetworkmanager.cpp
    testnetworkmanager.h
    testreleasemonitor.cpp
    testreleasemonitor.h
    testserveri18n.cpp
    testserveri18n.h
    testsettings.cpp
    testsettings.h
    teststatusicon.cpp
    teststatusicon.h
    testtasks.cpp
    testtasks.h
    testtemporarydir.cpp
    testtemporarydir.h
    testthemes.cpp
    testthemes.h
    testurlopener.cpp
    testurlopener.h
    websocket/testexponentialbackoffstrategy.cpp
    websocket/testexponentialbackoffstrategy.h
    websocket/testpushmessage.cpp
    websocket/testpushmessage.h
    websocket/testwebsockethandler.cpp
    websocket/testwebsockethandler.h
)

# Generate the version header
configure_file(${MVPN_SOURCE_DIR}/version.h.in ${CMAKE_CURRENT_BINARY_DIR}/version.h)
target_sources(auth_tests PRIVATE ${CMAKE_CURRENT_BINARY_DIR}/version.h)

# Unit test mock resources
target_sources(unit_tests PRIVATE
    addons/addons.qrc
    guides/guides.qrc
    servers/servers.qrc
    themes/themes.qrc
    tutorials/tutorials.qrc
)

## Add the tests to be run, one for each test class.
get_target_property(UTEST_SOURCES unit_tests SOURCES)
list(FILTER UTEST_SOURCES INCLUDE REGEX "test.*.h$")
foreach(filename ${UTEST_SOURCES})
    execute_process(
        OUTPUT_VARIABLE UTEST_CLASS_LIST
        OUTPUT_STRIP_TRAILING_WHITESPACE
        WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
        COMMAND python3 ${CMAKE_SOURCE_DIR}/scripts/tests/list_test_classes.py -p TestHelper ${filename}
    )

    foreach(UTEST_CLASS ${UTEST_CLASS_LIST})
        add_test(NAME ${UTEST_CLASS} COMMAND unit_tests ${UTEST_CLASS})
        set_property(TEST ${UTEST_CLASS} PROPERTY ENVIRONMENT LANG="en" LANGUAGE="en")
    endforeach()
endforeach()
