MESSAGE(STATUS "Micro compiler examples included")
MACRO(ADD_EXAMPLE TARGET_NAME)
    ADD_EXECUTABLE(${TARGET_NAME} ${TARGET_NAME}.cc ${ARGV})
    TARGET_LINK_LIBRARIES(${TARGET_NAME} PUBLIC ${PROJECT_NAME})
ENDMACRO()

GET_FILENAME_COMPONENT(HELLO_WORLD_MODEL
    "${TFLM_SRC}/examples/hello_world/model.cc"
    REALPATH BASE_DIR "${CMAKE_SOURCE_DIR}"
)

ADD_EXAMPLE(hello_world ${HELLO_WORLD_MODEL})
ADD_EXAMPLE(mobilenet mobilenet_v1_0_25_160_quantized.c gnu.c)
ADD_EXAMPLE(cifar10 cifar10_model.c truck.c)
