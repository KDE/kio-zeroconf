add_definitions(-DTRANSLATION_DOMAIN=\"kio5_zeroconf\")

add_library(kio_zeroconf MODULE)
set_target_properties(kio_zeroconf PROPERTIES
    OUTPUT_NAME "zeroconf"
)

target_sources(kio_zeroconf PRIVATE
    dnssd.cpp
)

target_link_libraries(kio_zeroconf PRIVATE
    KF${KF_MAJOR_VERSION}::DNSSD
    KF${KF_MAJOR_VERSION}::I18n
    KF${KF_MAJOR_VERSION}::KIOCore
)

install(TARGETS kio_zeroconf
        DESTINATION ${KDE_INSTALL_PLUGINDIR}/kf${QT_MAJOR_VERSION}/kio)

install(FILES zeroconf.desktop
        DESTINATION ${KDE_INSTALL_DATADIR}/remoteview)
