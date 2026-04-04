try:
    import gc, sys, os
    from Maix import GPIO
    from fpioa_manager import fm

    test_pin = 16
    fm.fpioa.set_function(test_pin, fm.fpioa.GPIO7)
    test_gpio = GPIO(GPIO.GPIO7, GPIO.IN, GPIO.PULL_UP)

    print("=== START PROGRAM ===")
    print("Welcome to MaixPy")

    # Kiểm tra test mode
    if test_gpio.value() == 0:
        print("PIN 16 pulled down, enter TEST MODE")
        import sensor

        sensor.reset()
        sensor.set_pixformat(sensor.RGB565)
        sensor.set_framesize(sensor.QVGA)
        sensor.run(1)

        print("Camera is running... (press reset to exit)")
        while True:
            img = sensor.snapshot()
            print("Captured one frame")

    # Hiển thị version firmware
    v = sys.implementation.version
    vers = 'V{}.{}.{} : maixpy.sipeed.com'.format(v[0], v[1], v[2])
    print("Firmware version:", vers)

    # Kiểm tra SD card
    try:
        os.listdir("/sd/.")
        print("SDcard is mounted, using SD!")
    except Exception as e:
        print("SDcard NOT mounted, using internal flash!")

    print("=== DONE ===")

    gc.collect()

finally:
    gc.collect()
