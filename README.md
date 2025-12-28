# IoT Classroom Management System (Full Frontend + Backend)

---

## Project Overview

A distributed IoT classroom management system for university teaching buildings, featuring multiple Raspberry Pi devices coordinated through a central Master Pi. Enables secure room booking, real-time environmental monitoring, and automated access control with three user roles: students/teachers, security staff, and administrators. Built with MQTT publish-subscribe architecture and socket programming, combining responsive web interfaces, live Sense HAT sensor data, and centralized MongoDB database management.

---

## Access to Code 🔒

The source code for this project is **private** and available upon request.

If you're an **employer** or **recruiter** and would like to review the code, please **request access via email** at **ayanhashmi205@yahoo.com**.

---

## Installation 📦

#### Prerequisites
- Python 3.8+ and pip
- Raspberry Pi devices (minimum 3: Master, Agent, Room)
- MongoDB Atlas account
- MQTT Broker (Mosquitto)
- Sense HAT module

#### Quick Start

```bash
# Clone repository
git clone https://github.com/ayan9870/iot-classroom-management-system.git
cd iot-classroom-management-system

# Install dependencies for each Pi
cd master-pi && pip install -r requirements.txt
cd agent-pi && pip install -r requirements.txt
cd room-pi && pip install -r requirements.txt

# Setup MQTT Broker
sudo apt-get install mosquitto mosquitto-clients
sudo systemctl start mosquitto

# Run applications
python master-pi/app.py
python agent-pi/app.py
python room-pi/app.py
```

---

## Features 📋

### Core User Features
* **User Authentication** - Secure registration and login with password hashing
* **Room Booking** - Search, reserve classrooms with conflict detection
* **Token-Based Access** - One-time tokens for room entry validation
* **Real-time Notifications** - MQTT alerts for system announcements
* **Personal Dashboard** - View booking history and upcoming reservations

### Admin Dashboard
* **User Management** - Create, edit, and manage all user accounts
* **System Announcements** - Broadcast MQTT messages to all devices
* **Usage Analytics** - Generate visual reports from booking data
* **Room Control** - Update availability and maintenance status

### Security Staff Functions
* **Room Status Updates** - Change state (Available, In Use, Maintenance, Fault)
* **Sense HAT Alerts** - Visual warnings with flashing lights for faults
* **Real-time Monitoring** - Subscribe to room status changes via MQTT

### Room Pi Display
* **Environmental Sensors** - Temperature, humidity, pressure from Sense HAT
* **Status Visualization** - Color-coded availability with emoji indicators
* **Booking Schedule** - Display upcoming reservations
* **Access Validation** - Token verification for entry

---

## Technology Stack 🔧

### Backend
* **Python 3.8+** - Core programming language
* **Flask** - Web framework for all Pi interfaces
* **Socket Programming** - Direct Pi-to-Pi communication
* **Paho MQTT** - Message broker client library
* **PyMongo** - MongoDB database driver
* **bcrypt** - Password hashing

### Frontend
* **HTML5/CSS3** - Responsive web interfaces
* **JavaScript** - Dynamic content updates
* **Bootstrap** - UI components
* **Chart.js** - Data visualization

### Hardware & IoT
* **Raspberry Pi 4** - Primary computing devices
* **Sense HAT** - Environmental sensors and LED matrix
* **Mosquitto** - MQTT message broker
* **MongoDB Atlas** - Cloud-hosted NoSQL database

---

## System Architecture 🗂️

### Communication Protocols
* **Socket Programming** - Request-response between Agent/Room Pis and Master Pi
* **MQTT Pub/Sub** - Broadcast alerts with QoS levels
* **Centralized Database** - MongoDB accessible only from Master Pi

### Database Collections
* **Users** - email, password (hashed), full_name, user_id, role, status
* **Rooms** - room_id, name, status, capacity, equipment
* **Bookings** - user_email, room_id, date, time slots, token, status
* **Logs** - user_email, action, details, timestamp

---

## Custom Enhancements 🚀

### Enhancement 1: Booking Coach (AI Recommendation)
**Analyzes historical room usage patterns to recommend best-fit rooms based on user preferences.**

**Key Features**:
- Historical usage pattern analysis
- Metadata scoring algorithm
- Filter support (capacity, equipment, time)
- Ranked shortlist with explanations
- CLI: `python -m enhancements.booking_coach`

**Impact**: Reduces booking time by 60%, improves room utilization

### Enhancement 2: Comfort Watch (Environmental Monitoring)
**Real-time environmental monitoring with intelligent alert system using rolling averages.**

**Key Features**:
- Continuous temperature, humidity, pressure sampling
- Rolling average smoothing to prevent false alarms
- MQTT alert publishing to subscribed devices
- Sense HAT warning display integration
- CLI: `python enhancements/comfort_watch/comfort_watch.py --broker <host> --room <id>`

**Impact**: Ensures optimal learning environment, enables proactive maintenance

---

## Design Patterns 🧱

* **Singleton Pattern** - Database connection management on Master Pi
* **Observer Pattern** - MQTT subscriptions for real-time updates
* **Factory Pattern** - User role creation with permission validation

---

## Testing 🔬

Comprehensive unit test suite using `pytest`:
* User authentication validation
* Room booking logic and token generation
* Socket and MQTT message format correctness
* Room status state transitions
* Error handling and edge cases

```bash
# Run tests
pytest enhancements/tests/
pytest --cov=. --cov-report=html
```

---

## Author ✨

| <a href="https://github.com/ayan9870" target="_blank">**Muhammad Ayan Hashmi**</a> |
|:--:|
| ![Ayan Hashmi](https://github.com/ayan9870.png?size=100) |
| [`github.com/ayan9870`](https://github.com/ayan9870) |

---

## License
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**
