# Sovol SV08 Klipper Configuration

## Printer Specifications

**Sovol SV08** - Modified 3D Printer Setup
- Sovol glass/metal enclosure with insulated walls
- Flashed with Klipper mainline firmware
- **Microswiss Flowtech Hotend** upgrade
- **Beacon Contact probe** with contact-based probing
- **Klipper Expander MCU** for fan control and chamber temperature monitoring
- **Mean Well LRS-350-24 and RS-25-5 power supplies** with DIN rail mounting
- **BTT Voron 2.4 bed** with kinematic mount, upgraded bed heater and PEI sheet
- **BTT SFS2 smart filament sensor** for advanced runout detection
- Relocated filament spool holder
- **'The Filter'** activated carbon air filtration system

---

## Configuration Overview

### 1. **LED Status System** (`options/led/hotend.cfg`)

Comprehensive LED status system using the hotend RGB LED for visual feedback:

- **15+ distinct status colors** for different printer states
- **Context-aware LED control** that changes automatically during operations
- **Chamber heating pulse animation** with smooth color transitions
- **Smart override protection** prevents conflicts during special operations

**Status Colors:**
- 🟢 Ready, Homing - Green
- 🔴 Busy, Error - Red variations  
- 🟠 Heating - Orange
- ⚪ Printing - Bright white
- 🟣 Leveling - Purple
- 🔵 Cleaning - Blue
- 🟡 Paused - Yellow
- Animated orange-to-red pulse during chamber heating

### 2. **Chamber Temperature Control** (`macros.cfg`)

Advanced chamber management following RepRap M141/M191 standards:

- **M141/M191 commands** for chamber temperature control
- **Intelligent heating logic** with automatic bed temperature adjustment
- **Material-specific presets**: PLA (0°C), PETG (30°C), ASA/ABS/TPU (35°C)
- **Progress tracking** with milestone reporting during heating
- **Animated LED feedback** during chamber conditioning
- **'The Filter' integration** with different speeds for heating vs. printing

### 3. **Enhanced Logging Framework** (`macros.cfg`)

Unified logging system for consistent status reporting:

- **Multi-channel output** to display, console, and LED simultaneously
- **Categorized messaging** (status, warning, error) with appropriate LED responses
- **Smart LED management** that respects active animations
- **Comprehensive operation tracking** throughout print workflows

### 4. **Improved Print Workflow** (`macros.cfg`)

Enhanced print process with better automation and feedback:

- **Parallel heating optimization** for faster startup
- **Material-aware chamber conditioning** with automatic temperature selection
- **Smart heat soak timing** that accounts for actual heating duration
- **BTT SFS2 filament detection** with advanced error handling
- **'The Filter' fan control** based on material requirements
- **Detailed status reporting** for every operation phase

### 5. **Probe System with Retry Logic** (`macros.cfg`)

Automatic retry capabilities for improved reliability:

- **Configurable retry attempts** with progressive delays
- **Detailed attempt tracking** and reporting
- **Automatic failure handling** with print cancellation
- **Beacon Contact integration** with enhanced error recovery
- **Two-stage QGL process** with coarse and fine tolerance passes

### 6. **Intelligent Fan Management** (`macros.cfg`)

Smart fan control throughout the system:

- **Dual-speed 'The Filter' operation**: slower during chamber heating, faster during printing
- **Material-based activation**: disabled for PLA, active for enclosed materials
- **Automatic shutdown delays**: 2-minute cooldown after print completion
- **Coordinated operation** with chamber temperature control

### 7. **Centralized Configuration** (`macros.cfg`)

Organized settings in a global variable system:

- **Material-specific chamber temperatures** in lookup tables
- **Configurable retry parameters** for all probe operations
- **Standardized parking positions** for different scenarios
- **Filament handling parameters** for loading/unloading operations
- **Fan speed presets** for various operational modes

### 8. **Hardware Integration Updates** (`printer.cfg`)

Updated configuration for new hardware components:

- **Klipper Expander** chamber sensor and fan control integration
- **'The Filter'** air filtration system configuration
- **BTT SFS2 smart filament sensor** for enhanced detection
- **Beacon Contact probe** with calibrated coefficients
- **Mean Well power supplies** for improved power delivery
- **Performance tuning**: increased max acceleration to 25,000 mm/s²
- **Optimized stepper settings** and TMC driver configuration

---

## Results

This configuration provides visual status feedback through LED colors, automated chamber conditioning for enclosed printing, intelligent retry logic for critical operations, and material-specific automation throughout the entire print workflow. The system handles most operations automatically while providing comprehensive status updates through logging and LED indicators.