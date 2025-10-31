# ARM Cortex-M Development Setup Guide

## 🎯 Quick Setup for ARM Development

This guide helps you set up your development environment for ARM Cortex-M programming with Raspberry Pi Pico.

## 🔧 Option 1: Simulation Only (Easiest)

**For trying projects without hardware:**

1. **Web Browser** - Any modern browser (Chrome, Firefox, Safari)
2. **Wokwi Account** - Free at [wokwi.com](https://wokwi.com)
3. **Click & Run** - Each project has a simulation link

**Benefits**: No installation, instant results, perfect for learning

## 🛠️ Option 2: Full Development Setup

**For building and flashing to real hardware:**

### Prerequisites
- **Raspberry Pi Pico** (RP2040 or RP2350)
- **USB Cable** (micro-USB for Pico)
- **Computer** (Windows, macOS, or Linux)

### Software Installation

#### 1. Install Pico SDK
```bash
# Clone Pico SDK
git clone https://github.com/raspberrypi/pico-sdk.git
cd pico-sdk
git submodule update --init

# Set environment variable
export PICO_SDK_PATH=/path/to/pico-sdk
```

#### 2. Install ARM GCC Toolchain
**macOS:**
```bash
brew install arm-none-eabi-gcc
```

**Ubuntu/Debian:**
```bash
sudo apt install gcc-arm-none-eabi
```

**Windows:**
Download from [ARM Developer](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm)

#### 3. Install Build Tools
```bash
# CMake and Make
sudo apt install cmake make  # Linux
brew install cmake          # macOS
```

#### 4. Install VS Code (Recommended)
- Download from [code.visualstudio.com](https://code.visualstudio.com)
- Install C/C++ extension
- Install CMake Tools extension

### Building Your First Project

1. **Clone this repository**
```bash
git clone https://github.com/yourusername/arm-cortex-m-tutorials.git
cd arm-cortex-m-tutorials
```

2. **Build a project**
```bash
cd projects/01-blink-led
mkdir build && cd build
cmake ..
make -j4
```

3. **Flash to Pico**
- Hold BOOTSEL button while connecting Pico
- Copy `blink.uf2` to RPI-RP2 drive
- Pico will reboot and run your code

## 🎓 Learning Path Recommendation

### Beginners
1. **Start with Wokwi** - Learn concepts without hardware complexity
2. **Try 3-5 projects** in simulation
3. **Get hardware** when comfortable with basics
4. **Build locally** for advanced features

### Experienced Developers
1. **Setup full environment** immediately
2. **Use Wokwi for quick testing**
3. **Build locally for optimization**
4. **Contribute to repository**

## 🔍 Troubleshooting

### Common Issues

**"PICO_SDK_PATH not found"**
- Set environment variable correctly
- Use absolute path to pico-sdk

**"arm-none-eabi-gcc not found"**
- Install ARM GCC toolchain
- Add to system PATH

**"Permission denied on /dev/ttyACM0"**
- Add user to dialout group: `sudo usermod -a -G dialout $USER`
- Logout and login again

**"Build fails with CMake errors"**
- Ensure CMake version 3.13+
- Check PICO_SDK_PATH is correct
- Try clean build: `rm -rf build && mkdir build`

### Getting Help

- **GitHub Issues** - Report problems in this repository
- **Raspberry Pi Forums** - Official Pico support
- **ARM Community** - ARM developer forums
- **Discord/Slack** - Real-time community help

## 📚 Additional Resources

### Official Documentation
- [Getting Started with Pico](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)
- [Pico SDK Documentation](https://raspberrypi.github.io/pico-sdk-doxygen/)
- [ARM Cortex-M Programming Guide](https://developer.arm.com/documentation/)

### Video Tutorials
- [Pico Setup Walkthrough](media/videos/) - Coming soon
- [First ARM Project](media/videos/) - Coming soon

### Community
- [GitHub Discussions](../../discussions) - Ask questions
- [Contributing Guide](../CONTRIBUTING.md) - Help improve tutorials

---

**Ready to start your ARM Cortex-M journey!** 🚀
