INCLUDE_DIRECTORIES(
	${CMAKE_SOURCE_DIR}
	${CMAKE_SOURCE_DIR}/scribus
)

SET(IMPORTSVM_PLUGIN_MOC_CLASSES
	importsvm.h
	importsvmplugin.h
)

SET(IMPORTSVM_PLUGIN_SOURCES
	importsvm.cpp
	importsvmplugin.cpp
)

SET(SCRIBUS_IMPORTSVM_PLUGIN "importsvm")

QT5_WRAP_CPP(IMPORTSVM_PLUGIN_MOC_SOURCES ${IMPORTSVM_PLUGIN_MOC_CLASSES})

ADD_LIBRARY(${SCRIBUS_IMPORTSVM_PLUGIN} MODULE ${IMPORTSVM_PLUGIN_SOURCES} ${IMPORTSVM_PLUGIN_MOC_SOURCES})

TARGET_LINK_LIBRARIES(${SCRIBUS_IMPORTSVM_PLUGIN} ${PLUGIN_LIBRARIES})

INSTALL(TARGETS ${SCRIBUS_IMPORTSVM_PLUGIN}
	LIBRARY
	DESTINATION ${PLUGINDIR}
	PERMISSIONS ${PLUGIN_PERMISSIONS}
)

ADD_DEPENDENCIES(${SCRIBUS_IMPORTSVM_PLUGIN} ${EXE_NAME})
