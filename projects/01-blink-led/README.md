# Blink LED - Your First ARM Cortex-M Project

## 🎯 What You'll Master

- ARM Cortex-M GPIO peripheral fundamentals
- Embedded programming workflow and structure
- Digital output control on ARM processors
- Pico SDK integration with ARM hardware

## 🧠 ARM Architecture Deep Dive

### Why This Matters for ARM Learning
This isn't just blinking an LED - you're learning how ARM Cortex-M processors control external hardware through memory-mapped peripherals. Every GPIO operation teaches you about ARM's efficient peripheral architecture.

### ARM Cortex-M GPIO Concepts
- **Memory-Mapped I/O**: GPIO registers are accessed like memory locations
- **Peripheral Clocking**: ARM peripherals need clock enabling before use
- **Register Configuration**: Direction, output, and input registers control behavior
- **Performance**: Single-cycle GPIO operations showcase ARM efficiency

## 🌐 Interactive Simulation

[🚀 Try Live Simulation](https://wokwi.com/projects/your-project-id)

*Experience ARM GPIO control without hardware - modify code and see instant results!*

## 🔧 Hardware Setup

### Components Needed
- Raspberry Pi Pico (ARM Cortex-M0+ RP2040)
- Standard LED (any color)
- 220Ω current-limiting resistor
- Breadboard for prototyping

### Circuit Connection Logic
```
GPIO Pin 2 → 220Ω Resistor → LED Anode (+) → LED Cathode (-) → Ground
```

**Why Pin 2?** Unlike many tutorials using pin 25 (onboard LED), we use pin 2 to learn external GPIO control - more relevant for real ARM projects.

## 💻 Code Walkthrough

### ARM Peripheral Initialization
```cpp
const uint LED_PIN = 2;              // GPIO pin selection

stdio_init_all();                    // Initialize ARM UART peripheral
gpio_init(LED_PIN);                  // Enable GPIO peripheral for pin 2
gpio_set_dir(LED_PIN, GPIO_OUT);     // Configure as output in GPIO direction register
```

**ARM Insight**: `gpio_init()` enables the GPIO peripheral clock and resets the pin configuration - essential ARM peripheral initialization pattern.

### Control Loop Implementation
```cpp
while (true) {
    gpio_put(LED_PIN, 1);            // Write HIGH to GPIO output register
    printf("LED illuminated\n");     // Debug via ARM UART peripheral
    sleep_ms(250);                   // Hardware timer-based delay
    
    gpio_put(LED_PIN, 0);            // Write LOW to GPIO output register  
    printf("LED extinguished\n");    // Serial debugging output
    sleep_ms(250);                   // Precise timing control
}
```

**Performance Note**: `gpio_put()` compiles to a single ARM instruction - showcasing the efficiency of ARM Cortex-M GPIO operations.

## 🏗️ Building Your ARM Project

### Development Environment
- **Toolchain**: ARM GCC cross-compiler
- **Build System**: CMake with ARM-specific configurations
- **SDK**: Raspberry Pi Pico SDK (ARM Cortex-M optimized)

### Compilation Process
```bash
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)
```

### Generated ARM Binaries
- `blink.elf` - ARM executable with debug symbols
- `blink.uf2` - UF2 bootloader format for Pico
- `blink.bin` - Raw ARM Cortex-M binary
- `blink.dis` - ARM assembly disassembly

## 🔍 ARM Architecture Insights

### GPIO Peripheral Details
- **RP2040 GPIO**: 30 programmable pins (GPIO0-GPIO29)
- **Voltage Levels**: 3.3V ARM standard logic levels
- **Drive Strength**: Configurable output current (2mA to 12mA)
- **Internal Resistors**: Built-in pull-up/pull-down options

### Memory Architecture
- **GPIO Base Address**: 0x40014000 (ARM memory map)
- **Register Access**: Direct memory-mapped peripheral control
- **Clock Domain**: GPIO runs on system clock (125MHz default)

## 🚀 Experimentation Ideas

### Modify and Learn
1. **Timing Variations**: Change delays to understand ARM timer precision
2. **Multiple Outputs**: Control several LEDs using different GPIO pins
3. **Pattern Generation**: Create complex blinking sequences
4. **Performance Testing**: Measure maximum toggle frequency

### ARM-Specific Experiments
- Monitor GPIO register values during operation
- Analyze generated ARM assembly code
- Test different compiler optimization levels
- Measure power consumption during GPIO operations

## 📚 Learning Progression

**Next ARM Concepts:**
- [Button Input](../button-input/) - Digital input and pull-up resistors
- [PWM Control](../../basic/02-pwm-basics/) - ARM timer peripherals for analog-like output
- [Multiple GPIO](../../basic/01-gpio-control/) - Parallel pin control and optimization

## 🎓 Key ARM Takeaways

1. **Peripheral Initialization**: Always enable and configure ARM peripherals before use
2. **Memory-Mapped I/O**: GPIO control through direct register access
3. **Efficient Operations**: Single-cycle GPIO operations demonstrate ARM performance
4. **Debug Integration**: UART provides essential debugging for ARM development
5. **Timing Precision**: Hardware timers ensure accurate delays in embedded systems

## 💡 Real-World Applications

This fundamental GPIO control pattern appears in:
- Industrial automation control systems
- IoT device status indicators  
- Automotive embedded systems
- Medical device user interfaces
- Consumer electronics feedback systems

## 📚 References & Credits

### Official Documentation
- [ARM Cortex-M0+ Technical Reference Manual](https://developer.arm.com/documentation/ddi0484/latest/) - ARM Ltd.
- [RP2040 Datasheet](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf) - Raspberry Pi Foundation
- [Raspberry Pi Pico SDK Documentation](https://raspberrypi.github.io/pico-sdk-doxygen/) - Raspberry Pi Foundation
- [GPIO Function Reference](https://raspberrypi.github.io/pico-sdk-doxygen/group__hardware__gpio.html) - Pico SDK

### Hardware Specifications
- [Raspberry Pi Pico Pinout](https://datasheets.raspberrypi.com/pico/Pico-R3-A4-Pinout.pdf) - Raspberry Pi Foundation
- [RP2040 GPIO Specifications](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf#page=12) - Section 2.19, Raspberry Pi Foundation

### Development Tools
- [Wokwi Online Simulator](https://wokwi.com/) - Wokwi Ltd.
- [ARM GCC Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm) - ARM Ltd.
- [CMake Build System](https://cmake.org/) - Kitware Inc.

### Educational Resources
- [ARM Architecture Reference Manual](https://developer.arm.com/documentation/ddi0403/latest/) - ARM Ltd.
- [Embedded Systems Programming Concepts](https://www.arm.com/resources/education/books) - ARM Education

### Standards & Protocols
- [GPIO Electrical Characteristics](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf#page=656) - RP2040 Datasheet Section 5.2.3

---

**Master ARM GPIO fundamentals - the foundation for all embedded projects!** 🚀
