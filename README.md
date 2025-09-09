# Code of the Sea
## Raspberry Pi Control Panel for Interactive Art Installation

**An art project collaboration between:**
- **Werapol Bejranonda** (Engineer) 
- **Eunji Lee** (Artist)

---

## 🎨 Project Overview

**Code of the Sea** is an interactive art installation that transforms a Raspberry Pi into a comprehensive control system for multimedia art experiences. The project bridges the technical and artistic realms, providing an intuitive web-based interface to control various hardware components including audio broadcasting, LED lighting systems, FM radio, and environmental monitoring.

This technical implementation serves as the backbone for immersive art installations where visitors can interact with and influence the artistic environment through various controls and real-time feedback systems.

## ✨ Features

### 🎵 **Broadcast System**
- **Audio Playback Control**: Play, pause, stop, next/previous track navigation
- **Multi-format Support**: MP3, WAV, OGG audio files
- **Web Interface**: Browser-based control panel for easy operation
- **Exhibition Ready**: Reliable track navigation without service interruptions
- **Auto-loop Capability**: Seamless audio experiences for installations

### 💡 **LED Lighting Control**
- **Dynamic Lighting**: Programmable LED strip control
- **Color Patterns**: Custom lighting sequences and effects
- **Real-time Control**: Immediate response to user interactions
- **Installation Integration**: Synchronized with other system components

### 📻 **FM Radio Integration**
- **Radio Control**: FM radio tuning and playback
- **Station Management**: Save and recall favorite stations
- **Audio Routing**: Integration with main audio system

### 🌡️ **Environmental Monitoring**
- **Hardware Monitoring**: CPU temperature, memory usage
- **System Health**: Real-time system status monitoring
- **Fan Control**: Automated cooling system management

### 🖥️ **Unified Web Interface**
- **Dashboard Mode**: Comprehensive control panel
- **Simple Mode**: Streamlined interface for basic operations  
- **Enhanced Mode**: Advanced controls for technical users
- **Mobile Responsive**: Works on tablets and smartphones

## 🏗️ System Architecture

```
Code of the Sea Control Panel
│
├── 🎵 Broadcast Module (broadcast/)
│   ├── Audio playback engine (mpg123 integration)
│   ├── Playlist management
│   ├── Media file scanning
│   └── Web API endpoints
│
├── 💡 LED Module (led/)
│   ├── Hardware control (GPIO/SPI)
│   ├── Pattern generation
│   ├── Color management
│   └── Effect scheduling
│
├── 📻 Radio Module (radio/)
│   ├── FM radio control
│   ├── Station presets
│   └── Audio routing
│
├── 🌡️ Hardware Module (fan/)
│   ├── Temperature monitoring
│   ├── Fan control
│   └── System metrics
│
├── 🔧 Core System (core/)
│   ├── Configuration management
│   ├── Service orchestration
│   ├── Logging system
│   └── Hardware abstraction
│
└── 🌐 Web Interface (templates/)
    ├── Dashboard UI
    ├── Control interfaces
    └── Status displays
```

## 🚀 Quick Start

### Prerequisites
- Raspberry Pi 4 (recommended) or Pi 3B+
- MicroSD card (32GB+ recommended)
- Audio output (speakers, headphones, or audio interface)
- Optional: LED strips, FM radio module, cooling fan

### Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/code-of-the-sea.git
   cd code-of-the-sea
   ```

2. **Run Setup Script**
   ```bash
   chmod +x setup.sh
   ./setup.sh
   ```

3. **Install as System Service**
   ```bash
   sudo ./install-service.sh
   ```

4. **Access the Control Panel**
   - Open your browser to `http://your-pi-ip:5000`
   - Default URL: `http://192.168.1.XXX:5000`

## 📁 Project Structure

```
code-of-the-sea/
│
├── README.md                    # This file
├── setup.sh                    # Initial setup script
├── install-service.sh           # System service installer
├── run.py                      # Application launcher
├── unified_app.py              # Main Flask application
├── cos-control-panel.service   # Systemd service configuration
│
├── broadcast/                  # Audio broadcast system
│   ├── broadcast_menu.py       # Main broadcast controller
│   ├── media/                  # Audio files directory
│   └── README.md              # Broadcast system docs
│
├── led/                       # LED lighting control
│   ├── lighting_menu.py       # LED controller
│   ├── lighting.py           # Hardware interface
│   └── led_config.json       # LED configuration
│
├── radio/                     # FM radio module
│   ├── fm-radio_menu.py      # Radio controller
│   └── radio_config.json     # Radio settings
│
├── fan/                       # Environmental control
│   ├── fan_mic_menu.py       # Fan and monitoring
│   └── fan_status.json       # System metrics
│
├── core/                      # Core system modules
│   ├── config_manager.py     # Configuration management
│   ├── service_manager.py    # Service orchestration
│   ├── hardware_monitor.py   # Hardware monitoring
│   └── logging_setup.py      # Logging configuration
│
├── templates/                 # Web interface templates
│   ├── dashboard.html        # Main dashboard
│   ├── simple.html          # Simplified interface
│   └── enhanced.html         # Advanced controls
│
└── media_samples/            # Example media files (not in repo)
```

## 🎛️ Usage Guide

### Web Interface

1. **Dashboard Mode** - Complete control panel with all features
2. **Simple Mode** - Basic controls for easy operation
3. **Enhanced Mode** - Advanced technical controls

### Broadcast System

- **Start Playback**: Click play button or use API endpoint
- **Track Navigation**: Use next/previous buttons
- **File Management**: Upload files to `broadcast/media/` directory
- **Status Monitoring**: Real-time playback status and playlist info

### LED Control

- **Pattern Selection**: Choose from predefined lighting patterns
- **Color Control**: RGB color picker and presets
- **Brightness**: Adjustable intensity levels
- **Timing**: Configure pattern speeds and transitions

### System Monitoring

- **Hardware Status**: CPU temperature, memory usage
- **Service Health**: Individual module status monitoring
- **Error Logging**: Comprehensive system logs

## 🔧 Configuration

### Main Configuration
Edit `unified_config.json` for global settings:

```json
{
    "mode": "dashboard",
    "debug": false,
    "auto_start_services": ["broadcast", "led"],
    "hardware": {
        "audio_output": "auto",
        "led_pin": 18,
        "fan_pin": 12
    }
}
```

### Module-Specific Configuration
Each module has its own configuration file in the respective directory.

## 🎨 Art Installation Setup

### For Exhibition Use

1. **Prepare Media Files**
   ```bash
   # Copy your audio files to the media directory
   cp /path/to/your/audio/* broadcast/media/
   ```

2. **Configure for Kiosk Mode**
   ```bash
   # Edit unified_config.json
   {
       "mode": "simple",
       "auto_start": true,
       "kiosk_mode": true
   }
   ```

3. **Install as Service**
   ```bash
   sudo ./install-service.sh
   ```

4. **Auto-start on Boot**
   - Service automatically starts when Pi boots
   - Accessible via web browser immediately
   - Fault-tolerant with automatic restart

### Hardware Integration

- **Audio**: Connect speakers or audio interface
- **LEDs**: Connect WS2812 LED strips to GPIO pin 18
- **Sensors**: Optional temperature/humidity sensors
- **Display**: Connect monitor for local display (optional)

## 🛠️ Development

### Adding New Modules

1. Create module directory in project root
2. Implement module menu class following existing patterns
3. Add configuration files
4. Register in `run.py` and `unified_app.py`
5. Create web interface templates

### API Endpoints

The system provides RESTful API endpoints for all controls:

```bash
# Broadcast controls
POST /broadcast_control/play
POST /broadcast_control/pause  
POST /broadcast_control/next
GET  /broadcast_status

# LED controls
POST /led_control/pattern/<pattern_name>
POST /led_control/color
GET  /led_status

# System status
GET  /system_status
GET  /service_health
```

## 🔍 Troubleshooting

### Common Issues

**Service Won't Start**
```bash
# Check service status
sudo systemctl status cos-control-panel

# View logs
sudo journalctl -u cos-control-panel -f

# Manual start for debugging
cd /home/payas/cos
python run.py unified
```

**Audio Not Playing**
```bash
# Check audio system
aplay -l

# Test audio output
speaker-test -t wav

# Check mpg123 installation
which mpg123
```

**LED Not Working**
```bash
# Check GPIO permissions
sudo usermod -a -G gpio $USER

# Test LED connection
python -c "import RPi.GPIO as GPIO; GPIO.setmode(GPIO.BCM); GPIO.setup(18, GPIO.OUT)"
```

## 📜 License

This project is open-source and available under the MIT License. See LICENSE file for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests, report issues, or suggest improvements.

### Development Setup
```bash
# Clone repository
git clone https://github.com/your-username/code-of-the-sea.git

# Install dependencies
cd code-of-the-sea
python -m venv venv
source venv/bin/activate
pip install flask psutil

# Run in development mode
python run.py unified
```

## 📞 Support

For technical support or artistic collaboration inquiries:

- **Technical Issues**: Create an issue on GitHub
- **Art Project Inquiries**: Contact the collaborative team
- **Installation Support**: See troubleshooting section above

## 🎯 Roadmap

### Planned Features
- [ ] Mobile app for remote control
- [ ] Advanced scheduling system
- [ ] Multi-device synchronization
- [ ] Cloud-based configuration backup
- [ ] Extended hardware module support
- [ ] Advanced audio effects processing
- [ ] Integration with external art installations

### Version History
- **v1.0** - Initial release with core functionality
- **v1.1** - Enhanced broadcast system with reliable track navigation
- **v1.2** - Improved LED control and web interface

---

**Code of the Sea** represents the intersection of technology and art, providing a robust platform for interactive installations while maintaining the flexibility needed for creative expression. The collaboration between engineering precision and artistic vision creates possibilities for unique and engaging art experiences.