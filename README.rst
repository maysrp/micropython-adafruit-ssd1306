ESP32 ssd_1306 OLED


FROM https://github.com/adafruit/micropython-adafruit-ssd1306

|OLED|ESP32|
|-|-|
|SCK|D18|
|SDA|D23|
|RES|D15|
|DC|D2|
|CS|D4|
|VCC(VDD)|3v3|
|GDN|GDN|


```
from machine import Pin,SPI 
hspi = SPI(2, baudrate=80000000, polarity=0, phase=0, sck=Pin(18), mosi=Pin(23),miso=Pin(19))
xdc=machine.Pin(02,Pin.OUT)
res=machine.Pin(5,Pin.OUT)
cs=machine.Pin(04,Pin.OUT)
display = ssd1306.SSD1306_SPI(128, 64, hspi,xdc,res,cs)
display.init_display()
display.pixel(1,3,1)
display.line(22,33,45,55,1)
display.hline(22,13,25,1)
display.vline(9,31,15,1)
display.text('Hello world',10,10,0)
display.show()
display.fill(0)
display.show()
display.fill(1)
display.show()
```




DEPRECATED LIBRARY micropython-adafruit-ssd1306
===============================================

This library has been deprecated! We are leaving this up for historical and research purposes but archiving the repository.

We are now only supporting CircuitPython libraries.

Check out this library if you're interested in using the SSD1306: https://github.com/adafruit/Adafruit_CircuitPython_SSD1306

MicroPython driver for SSD1306 OLED displays.

This driver is based on the SSD1306 driver in the MicroPython source but differs by supporting hardware I2C interfaces (like on the SAMD21 MicroPython port).
