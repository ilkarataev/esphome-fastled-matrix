# esphome-fastled-matrix
component for writing effects for LED matrixes

**At the moment of commit it works only with esphome:dev branch!**
For build with this component you need build in dev enviroment  
Can use docker:  
``` docker run --rm --net=host -it -p 6052:6052 -v "${PWD}"/:/config esphome/esphome:dev```  
Where is ${PWD}"/ is pwd with yaml.  
You need to add custom_components path in the same directory with yaml.  
Build and upload it from http://127.0.0.1:6052   

## Example usage:

``` yaml
# important to add component here
fastled_matrix_effects:
  
light:
  # matrix platfor for light
  - platform: fastled_matrix_clockless
    id: matrixcontroller_led_matrix
    name: "LedMatrix"
    chipset: WS2812B
    pin: GPIO13
    max_refresh_rate: 30ms
    num_leds: 256
    rgb_order: GRB
    width: 16
    height: 16
    rotation: 3
    max_brightness: 100
    max_current: 500
    type:
      - NEO_MATRIX_BOTTOM
      - NEO_MATRIX_RIGHT
      - NEO_MATRIX_COLUMNS
      - NEO_MATRIX_ZIGZAG
    effects:
      - fire:
          hue: 1
          sparkles: true
```

You can check available options for `type` parameter here: https://github.com/marcmerlin/Framebuffer_GFX/blob/master/Framebuffer_GFX.h#L43

Combine these values to create configuration matching your led matrix.

Possible values for `rotation` parameter are 0-3: https://github.com/adafruit/Adafruit-GFX-Library/blob/master/Adafruit_GFX.cpp#L1310
