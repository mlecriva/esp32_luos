set(include_dirs port/include 
                 luos_engine/engine/bootloader
                 luos_engine/engine/core/inc
                 luos_engine/engine/OD
                 luos_engine/engine/profiles/motor
                 luos_engine/engine/profiles/servo_motor
                 luos_engine/engine/profiles/state
                 luos_engine/engine/profiles/voltage
                 luos_engine/network/robus/inc
                 luos_engine/engine/HAL/ESP32
                 luos_engine/network/robus/HAL/ESP32
                 luos_engine/tool_services/gate
                 luos_engine/tool_services/gate/TinyJSON
                 luos_engine/tool_services/inspector
                 luos_engine/tool_services/pipe
                 luos_engine/tool_services/pipe/SERIAL/ESP32)

set(srcs
    "luos_engine/engine/bootloader/bootloader_core.c"
    "luos_engine/engine/core/src/luos_engine.c"
    "luos_engine/engine/core/src/luos_utils.c"
    "luos_engine/engine/core/src/profile_core.c"
    "luos_engine/engine/core/src/routing_table.c"
    "luos_engine/engine/core/src/streaming.c"
    "luos_engine/engine/core/src/timestamp.c"
    "luos_engine/engine/profiles/motor/profile_motor.c"
    "luos_engine/engine/profiles/servo_motor/profile_servo_motor.c"
    "luos_engine/engine/profiles/state/profile_state.c"
    "luos_engine/engine/profiles/voltage/profile_voltage.c"
    "luos_engine/engine/HAL/ESP32/luos_hal.c"
    "luos_engine/network/robus/src/msg_alloc.c"
    "luos_engine/network/robus/src/port_manager.c"
    "luos_engine/network/robus/src/reception.c"
    "luos_engine/network/robus/src/robus.c"
    "luos_engine/network/robus/src/topic.c"
    "luos_engine/network/robus/src/transmission.c"
    "luos_engine/network/robus/HAL/ESP32/robus_hal.c"
    "luos_engine/tool_services/gate/data_manager.c"
    "luos_engine/tool_services/gate/gate.c"
    "luos_engine/tool_services/gate/pipe_link.c"
    "luos_engine/tool_services/gate/TinyJSON/bootloader_ex.c"
    "luos_engine/tool_services/gate/TinyJSON/convert.c"
    "luos_engine/tool_services/gate/TinyJSON/tiny-json.c"
    "luos_engine/tool_services/inspector/data_manager.c"
    "luos_engine/tool_services/inspector/inspector.c"
    "luos_engine/tool_services/inspector/pipe_link.c"
    "luos_engine/tool_services/pipe/pipe.c"
    "luos_engine/tool_services/pipe/pipe_buffer.c"
    "luos_engine/tool_services/pipe/SERIAL/ESP32/pipe_com.c")

idf_component_register(SRCS "${srcs}"
                    INCLUDE_DIRS "${include_dirs}")
                
target_compile_options(${COMPONENT_LIB} PRIVATE "-Wno-error=restrict" "-Wno-error=format-overflow")
target_compile_definitions(${COMPONENT_LIB} PRIVATE "-DLUOSHAL=ESP32 -DGATEFORMAT=TinyJSON -DPIPEMODE=SERIAL -D PIPEHAL=ESP32")  
