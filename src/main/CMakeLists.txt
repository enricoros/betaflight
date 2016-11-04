cmake_minimum_required(VERSION 3.6)
project(main)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# IRCFUSIONF3
include_directories(. target/IRCFUSIONF3)


#F3_TARGETS   += $(TARGET)
add_definitions(-DF3_TARGETS=IRCFUSIONF3)
# makefile expansion
add_definitions(-DFLASH_SIZE=256)
add_definitions(-DONBOARDFLASH)

#FEATURES     = VCP ONBOARDFLASH
include_directories(vcp)

#TARGET_FLAGS = -DSPRACINGF3
add_definitions(-DSPRACINGF3)

# IRC-specific files
set(IRCFUSIONF3_FILES
    drivers/accgyro_mpu.c
    drivers/accgyro_mpu6050.c
    drivers/barometer_bmp085.c)


# all the rest
set(SOURCE_FILES
    blackbox/blackbox.c
    blackbox/blackbox.h
    blackbox/blackbox_fielddefs.h
    blackbox/blackbox_io.c
    blackbox/blackbox_io.h
    build/atomic.h
    build/build_config.c
    build/build_config.h
    build/debug.c
    build/debug.h
    build/version.c
    build/version.h
    common/axis.h
    common/color.h
    common/colorconversion.c
    common/colorconversion.h
    common/encoding.c
    common/encoding.h
    common/filter.c
    common/filter.h
    common/maths.c
    common/maths.h
    common/printf.c
    common/printf.h
    common/streambuf.c
    common/streambuf.h
    common/typeconversion.c
    common/typeconversion.h
    common/utils.h
    config/config_eeprom.c
    config/config_eeprom.h
    config/config_master.h
    config/config_profile.h
    config/config_unittest.h
    config/feature.c
#    config/feature.h
    config/parameter_group.c
    config/parameter_group.h
    config/parameter_group_ids.h
    drivers/accgyro.h
    drivers/accgyro_adxl345.c
    drivers/accgyro_adxl345.h
    drivers/accgyro_bma280.c
    drivers/accgyro_bma280.h
    drivers/accgyro_l3g4200d.c
    drivers/accgyro_l3g4200d.h
    drivers/accgyro_l3gd20.c
    drivers/accgyro_l3gd20.h
    drivers/accgyro_lsm303dlhc.c
    drivers/accgyro_lsm303dlhc.h
    drivers/accgyro_mma845x.c
    drivers/accgyro_mma845x.h
    drivers/accgyro_mpu.c
    drivers/accgyro_mpu.h
#    drivers/accgyro_mpu3050.c
#    drivers/accgyro_mpu3050.h
#    drivers/accgyro_mpu6050.c
#    drivers/accgyro_mpu6050.h
#    drivers/accgyro_mpu6500.c
#    drivers/accgyro_mpu6500.h
    drivers/accgyro_spi_icm20689.c
    drivers/accgyro_spi_icm20689.h
    drivers/accgyro_spi_mpu6000.c
    drivers/accgyro_spi_mpu6000.h
    drivers/accgyro_spi_mpu6500.c
    drivers/accgyro_spi_mpu6500.h
    drivers/accgyro_spi_mpu9250.c
    drivers/accgyro_spi_mpu9250.h
    drivers/adc.c
    drivers/adc.h
    drivers/adc_impl.h
#    drivers/adc_stm32f10x.c
    drivers/adc_stm32f30x.c
 #   drivers/adc_stm32f4xx.c
  #  drivers/adc_stm32f7xx.c
    drivers/barometer.h
#    drivers/barometer_bmp085.c
#    drivers/barometer_bmp085.h
#    drivers/barometer_bmp280.c
#    drivers/barometer_bmp280.h
#    drivers/barometer_ms5611.c
#    drivers/barometer_ms5611.h
#    drivers/barometer_spi_bmp280.c
#    drivers/barometer_spi_bmp280.h
    drivers/buf_writer.c
    drivers/buf_writer.h
    drivers/bus_i2c.h
    drivers/bus_i2c_hal.c
    drivers/bus_i2c_soft.c
#    drivers/bus_i2c_stm32f10x.c
    drivers/bus_i2c_stm32f30x.c
    drivers/bus_spi.c
    drivers/bus_spi.h
    drivers/bus_spi_hal.c
    drivers/bus_spi_soft.c
    drivers/bus_spi_soft.h
    drivers/compass.h
    drivers/compass_ak8963.c
    drivers/compass_ak8963.h
    drivers/compass_ak8975.c
    drivers/compass_ak8975.h
    drivers/compass_hmc5883l.c
    drivers/compass_hmc5883l.h
    drivers/display_ug2864hsweg01.c
    drivers/display_ug2864hsweg01.h
    drivers/dma.c
    drivers/dma.h
    drivers/dma_stm32f4xx.c
#    drivers/dma_stm32f7xx.c
    drivers/exti.c
    drivers/exti.h
    drivers/flash.h
    drivers/flash_m25p16.c
    drivers/flash_m25p16.h
    drivers/gpio.h
#    drivers/gpio_stm32f10x.c
    drivers/gpio_stm32f30x.c
#    drivers/gpio_stm32f4xx.c
#    drivers/gpio_stm32f7xx.c
    drivers/gyro_sync.c
    drivers/gyro_sync.h
    drivers/inverter.c
    drivers/inverter.h
    drivers/io.c
    drivers/io.h
    drivers/io_def.h
    drivers/io_def_generated.h
    drivers/io_impl.h
    drivers/io_types.h
    drivers/light_led.c
    drivers/light_led.h
    drivers/light_ws2811strip.c
    drivers/light_ws2811strip.h
    drivers/light_ws2811strip_hal.c
#    drivers/light_ws2811strip_stm32f10x.c
    drivers/light_ws2811strip_stm32f30x.c
#    drivers/light_ws2811strip_stm32f4xx.c
    drivers/max7456.c
    drivers/max7456.h
    drivers/max7456_symbols.h
    drivers/nvic.h
    drivers/pwm_output.c
    drivers/pwm_output.h
    drivers/pwm_output_hal.c
    drivers/pwm_output_stm32f3xx.c
#    drivers/pwm_output_stm32f4xx.c
#    drivers/pwm_output_stm32f7xx.c
    drivers/pwm_rx.c
    drivers/pwm_rx.h
    drivers/rcc.c
    drivers/rcc.h
    drivers/rcc_types.h
    drivers/resource.h
    drivers/rx_nrf24l01.c
    drivers/rx_nrf24l01.h
    drivers/rx_spi.c
    drivers/rx_spi.h
    drivers/rx_xn297.c
    drivers/rx_xn297.h
    drivers/sdcard.c
    drivers/sdcard.h
    drivers/sdcard_standard.c
    drivers/sdcard_standard.h
    drivers/sensor.h
    drivers/serial.c
    drivers/serial.h
    drivers/serial_escserial.c
    drivers/serial_escserial.h
    drivers/serial_softserial.c
    drivers/serial_softserial.h
    drivers/serial_uart.c
    drivers/serial_uart.h
    drivers/serial_uart_hal.c
    drivers/serial_uart_impl.h
#    drivers/serial_uart_stm32f10x.c
    drivers/serial_uart_stm32f30x.c
    #drivers/serial_uart_stm32f4xx.c
    #drivers/serial_uart_stm32f7xx.c
    drivers/serial_usb_vcp.c
    drivers/serial_usb_vcp.h
    drivers/serial_usb_vcp_hal.c
    drivers/sonar_hcsr04.c
    drivers/sonar_hcsr04.h
    drivers/sound_beeper.c
    drivers/sound_beeper.h
    drivers/system.c
    drivers/system.h
    #drivers/system_stm32f10x.c
    drivers/system_stm32f30x.c
    #drivers/system_stm32f4xx.c
    #drivers/system_stm32f7xx.c
    drivers/timer.c
    drivers/timer.h
    drivers/timer_hal.c
    drivers/timer_impl.h
#    drivers/timer_stm32f10x.c
    #drivers/timer_stm32f10x.h
    drivers/timer_stm32f30x.c
    drivers/timer_stm32f30x.h
#    drivers/timer_stm32f4xx.c
#    drivers/timer_stm32f4xx.h
#    drivers/timer_stm32f7xx.c
#    drivers/timer_stm32f7xx.h
    drivers/transponder_ir.c
    drivers/transponder_ir.h
    drivers/transponder_ir_stm32f30x.c
    drivers/usb_detection.c
    drivers/usb_detection.h
    drivers/usb_io.c
    drivers/usb_io.h
    drivers/vtx_rtc6705.c
    drivers/vtx_rtc6705.h
    drivers/vtx_soft_spi_rtc6705.c
    drivers/vtx_soft_spi_rtc6705.h
    fc/config.c
    fc/config.h
    fc/fc_msp.c
    fc/fc_msp.h
    fc/fc_tasks.c
    fc/fc_tasks.h
    fc/mw.c
    fc/mw.h
    fc/rc_controls.c
    fc/rc_controls.h
    fc/rc_curves.c
    fc/rc_curves.h
    fc/runtime_config.c
    fc/runtime_config.h
    flight/altitudehold.c
    flight/altitudehold.h
    flight/failsafe.c
    flight/failsafe.h
    flight/gps_conversion.c
    flight/gps_conversion.h
    flight/gtune.c
    flight/gtune.h
    flight/imu.c
    flight/imu.h
    flight/mixer.c
    flight/mixer.h
    flight/navigation.c
    flight/navigation.h
    flight/pid.c
    flight/pid.h
    flight/servos.c
    flight/servos.h
    io/asyncfatfs/asyncfatfs.c
    io/asyncfatfs/asyncfatfs.h
    io/asyncfatfs/fat_standard.c
    io/asyncfatfs/fat_standard.h
    io/beeper.c
    io/beeper.h
    io/dashboard.c
    io/dashboard.h
    io/flashfs.c
    io/flashfs.h
    io/gimbal.h
    io/gps.c
    io/gps.h
    io/ledstrip.c
    io/ledstrip.h
    io/motors.h
    io/osd.c
    io/osd.h
    io/serial.c
    io/serial.h
    io/serial_4way.c
    io/serial_4way.h
    io/serial_4way_avrootloader.c
    io/serial_4way_avrootloader.h
    io/serial_4way_impl.h
    io/serial_4way_stk500v2.c
    io/serial_4way_stk500v2.h
    io/serial_cli.c
    io/serial_cli.h
    io/servos.h
    io/statusindicator.c
    io/statusindicator.h
    io/transponder_ir.c
    io/transponder_ir.h
    io/vtx.c
    io/vtx.h
    msp/msp.h
    msp/msp_protocol.h
    msp/msp_serial.c
    msp/msp_serial.h
    rx/ibus.c
    rx/ibus.h
    rx/jetiexbus.c
    rx/jetiexbus.h
    rx/msp.c
    rx/msp.h
    rx/nrf24_cx10.c
    rx/nrf24_cx10.h
    rx/nrf24_h8_3d.c
    rx/nrf24_h8_3d.h
    rx/nrf24_inav.c
    rx/nrf24_inav.h
    rx/nrf24_syma.c
    rx/nrf24_syma.h
    rx/nrf24_v202.c
    rx/nrf24_v202.h
    rx/pwm.c
    rx/pwm.h
    rx/rx.c
    rx/rx.h
    rx/rx_spi.c
    rx/rx_spi.h
    rx/sbus.c
    rx/sbus.h
    rx/spektrum.c
    rx/spektrum.h
    rx/sumd.c
    rx/sumd.h
    rx/sumh.c
    rx/sumh.h
    rx/xbus.c
    rx/xbus.h
    scheduler/scheduler.c
    scheduler/scheduler.h
    sensors/acceleration.c
    sensors/acceleration.h
    sensors/barometer.c
    sensors/barometer.h
    sensors/battery.c
    sensors/battery.h
    sensors/boardalignment.c
    sensors/boardalignment.h
    sensors/compass.c
    sensors/compass.h
    sensors/gyro.c
    sensors/gyro.h
    sensors/initialisation.c
    sensors/initialisation.h
    sensors/sensors.h
    sensors/sonar.c
    sensors/sonar.h
#    target/AIORACERF3/target.c
#    target/AIORACERF3/target.h
#    target/AIR32/target.c
#    target/AIR32/target.h
#    target/AIRHEROF3/target.c
#    target/AIRHEROF3/target.h
#    target/ALIENFLIGHTF1/config.c
#    target/ALIENFLIGHTF1/target.c
#    target/ALIENFLIGHTF1/target.h
#    target/ALIENFLIGHTF3/config.c
#    target/ALIENFLIGHTF3/hardware_revision.c
#    target/ALIENFLIGHTF3/hardware_revision.h
#    target/ALIENFLIGHTF3/target.c
#    target/ALIENFLIGHTF3/target.h
#    target/ALIENFLIGHTF4/config.c
#    target/ALIENFLIGHTF4/target.c
#    target/ALIENFLIGHTF4/target.h
#    target/ANYFCF7/stm32f7xx_hal_conf.h
#    target/ANYFCF7/target.c
#    target/ANYFCF7/target.h
#    target/BETAFLIGHTF3/target.c
#    target/BETAFLIGHTF3/target.h
#    target/BLUEJAYF4/config.c
#    target/BLUEJAYF4/hardware_revision.c
#    target/BLUEJAYF4/hardware_revision.h
#    target/BLUEJAYF4/target.c
#    target/BLUEJAYF4/target.h
#    target/CC3D/target.c
#    target/CC3D/target.h
#    target/CHEBUZZF3/target.c
#    target/CHEBUZZF3/target.h
#    target/CJMCU/hardware_revision.c
#    target/CJMCU/hardware_revision.h
#    target/CJMCU/target.c
#    target/CJMCU/target.h
#    target/COLIBRI/config.c
#    target/COLIBRI/target.c
#    target/COLIBRI/target.h
#    target/COLIBRI_RACE/bus_bst.h
#    target/COLIBRI_RACE/bus_bst_stm32f30x.c
#    target/COLIBRI_RACE/config.c
#    target/COLIBRI_RACE/i2c_bst.c
#    target/COLIBRI_RACE/i2c_bst.h
#    target/COLIBRI_RACE/target.c
#    target/COLIBRI_RACE/target.h
#    target/DOGE/target.c
#    target/DOGE/target.h
#    target/F4BY/target.c
#    target/F4BY/target.h
#    target/FURYF3/target.c
#    target/FURYF3/target.h
#    target/FURYF4/target.c
#    target/FURYF4/target.h
#    target/FURYF7/stm32f7xx_hal_conf.h
#    target/FURYF7/target.c
#    target/FURYF7/target.h
#    target/IMPULSERCF3/target.c
#    target/IMPULSERCF3/target.h
    target/IRCFUSIONF3/target.c
    target/IRCFUSIONF3/target.h
#    target/ISHAPEDF3/target.c
#    target/ISHAPEDF3/target.h
#    target/KISSFC/target.c
#    target/KISSFC/target.h
#    target/LUX_RACE/target.c
#    target/LUX_RACE/target.h
#    target/MICROSCISKY/target.c
#    target/MICROSCISKY/target.h
#    target/MOTOLAB/config.c
#    target/MOTOLAB/target.c
#    target/MOTOLAB/target.h
#    target/NAZE/config.c
#    target/NAZE/hardware_revision.c
#    target/NAZE/hardware_revision.h
#    target/NAZE/target.c
#    target/NAZE/target.h
#    target/OMNIBUS/target.c
#    target/OMNIBUS/target.h
#    target/OMNIBUSF4/target.c
#    target/OMNIBUSF4/target.h
#    target/PIKOBLX/target.c
#    target/PIKOBLX/target.h
#    target/RACEBASE/config.c
#    target/RACEBASE/hardware_revision.c
#    target/RACEBASE/hardware_revision.h
#    target/RACEBASE/target.c
#    target/RACEBASE/target.h
#    target/RCEXPLORERF3/target.c
#    target/RCEXPLORERF3/target.h
#    target/REVO/target.c
#    target/REVO/target.h
#    target/REVONANO/target.c
#    target/REVONANO/target.h
#    target/RMDO/target.c
#    target/RMDO/target.h
#    target/SINGULARITY/target.c
#    target/SINGULARITY/target.h
#    target/SIRINFPV/target.c
#    target/SIRINFPV/target.h
#    target/SOULF4/target.c
#    target/SOULF4/target.h
#    target/SPARKY/target.c
#    target/SPARKY/target.h
#    target/SPARKY2/target.c
#    target/SPARKY2/target.h
#    target/SPRACINGF3/target.c
#    target/SPRACINGF3/target.h
#    target/SPRACINGF3EVO/target.c
#    target/SPRACINGF3EVO/target.h
#    target/SPRACINGF3MINI/target.c
#    target/SPRACINGF3MINI/target.h
#    target/STM32F3DISCOVERY/target.c
#    target/STM32F3DISCOVERY/target.h
#    target/VRRACE/target.c
#    target/VRRACE/target.h
#    target/X_RACERSPI/target.c
#    target/X_RACERSPI/target.h
#    target/YUPIF4/target.c
#    target/YUPIF4/target.h
#    target/ZCOREF3/target.c
#    target/ZCOREF3/target.h
    target/common.h
    target/system_stm32f30x.c
    target/system_stm32f30x.h
#    target/system_stm32f4xx.c
#    target/system_stm32f4xx.h
#    target/system_stm32f7xx.c
#    target/system_stm32f7xx.h
    telemetry/frsky.c
    telemetry/frsky.h
    telemetry/hott.c
    telemetry/hott.h
    telemetry/jetiexbus.h
    telemetry/ltm.c
    telemetry/ltm.h
    telemetry/mavlink.c
    telemetry/mavlink.h
    telemetry/smartport.c
    telemetry/smartport.h
    telemetry/telemetry.c
    telemetry/telemetry.h
    vcp/hw_config.c
    vcp/hw_config.h
    vcp/platform_config.h
    vcp/stm32_it.c
    vcp/stm32_it.h
    vcp/usb_conf.h
    vcp/usb_desc.c
    vcp/usb_desc.h
    vcp/usb_endp.c
    vcp/usb_istr.c
    vcp/usb_istr.h
    vcp/usb_prop.c
    vcp/usb_prop.h
    vcp/usb_pwr.c
    vcp/usb_pwr.h
    vcp_hal/usbd_cdc_interface.c
    vcp_hal/usbd_cdc_interface.h
    vcp_hal/usbd_conf.c
    vcp_hal/usbd_conf.h
    vcp_hal/usbd_desc.c
    vcp_hal/usbd_desc.h
#    vcpf4/stm32f4xx_it.c
#    vcpf4/stm32f4xx_it.h
    vcpf4/usb_bsp.c
    vcpf4/usb_conf.h
    vcpf4/usbd_cdc_vcp.c
    vcpf4/usbd_cdc_vcp.h
    vcpf4/usbd_conf.h
    vcpf4/usbd_desc.c
    vcpf4/usbd_desc.h
    vcpf4/usbd_usr.c
    main.c
    platform.h)

add_executable(main ${SOURCE_FILES} ${IRCFUSIONF3_FILES})