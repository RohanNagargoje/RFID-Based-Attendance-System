# RFID-Based Attendance System (ESP32 + SD Card + RTC + Python)

A smart and affordable attendance system built using the ESP32, RFID (RC522), RTC module (DS3231/DS1307), and an SD card to log attendance data. This system is designed for offline use and can later be expanded to support online databases or dashboards. A Python-based backend is optionally included for local data logging and future integrations.

---

## Features

- Accurate time-stamping using RTC module (DS3231 or DS1307)
- RFID card scanning via RC522 module
- Logs attendance data to SD card in CSV format
- Optional Python backend for storing data in SQLite
- Designed to be extended to cloud storage or web dashboards
- Fast, reliable, and fully offline capable

---

## Tech Stack

| Component       | Details                            |
|----------------|-------------------------------------|
| Microcontroller | ESP32                              |
| RFID Reader     | RC522 (SPI interface)              |
| RTC Module      | DS3231 or DS1307 (I2C interface)   |
| Storage         | Micro SD card module (SPI)         |
| Firmware Lang   | Arduino (C/C++)                    |
| Backend Lang    | Python 3.x                         |
| Local Database  | SQLite (optional)                  |

---

## System Overview

````

You can find diagrams and visuals in the `docs/` folder once added.

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/RFID-Based-Attendance-System.git
cd RFID-Based-Attendance-System
````

### 2. Hardware Setup

* Connect RC522, RTC Module (DS3231 or DS1307), and SD Card Module to the ESP32.
* RC522 and SD card use SPI interface.
* RTC uses I2C interface (typically SDA = GPIO 21, SCL = GPIO 22).
* Power the system via USB or external 5V.
* Refer to the wiring diagram in `hardware/connection_diagram.png`.

### 3. Upload Firmware

* Navigate to the `firmware/` folder.
* Open the `.ino` file in Arduino IDE.
* Select ESP32 Dev Module as the board.
* Install required libraries:

  * MFRC522
  * SD
  * Wire
  * RTClib by Adafruit
* Upload the code to your ESP32.

The firmware will:

* Read RFID UID when a tag is scanned
* Retrieve current time from the RTC module
* Log UID and timestamp to the SD card
* Optionally send data over serial to a Python logger

### 4. Python Logger Setup (Optional)

* Navigate to the `software/` folder.
* Install dependencies:

```bash
pip install -r requirements.txt
```

* Run the logger script (reads serial data from ESP32):

```bash
python logger.py
```

* Make sure the correct COM port is used and matches your OS.

---

## SD Card Data Format

The system logs data in a file on the SD card named `attendance.csv` with the following format:

```
Timestamp,UID
2025-08-07 08:15:23,A1B2C3D4
2025-08-07 08:16:10,D4C3B2A1
```

* Timestamps are sourced from the RTC for accuracy
* UID is the unique identifier from the RFID tag

---

## Project Structure

```
RFID-Based-Attendance-System/
├── hardware/               → Circuit diagrams, ESP32 wiring, photos
├── firmware/               → ESP32 code (RFID, RTC, SD logging)
├── software/               → Python app to log and store data locally
│   └── requirements.txt    → Python dependencies
├── database/               → SQLite schema and queries (optional)
├── docs/                   → System architecture, screenshots, images
├── .gitignore              → Ignore files/folders for cleaner commits
├── LICENSE                 → Open-source license (MIT)
└── README.md               → This file
```

---

## Future Improvements

* Connect to Firebase or MySQL for cloud storage
* Create a web dashboard to view attendance reports
* Add buzzer or OLED for real-time feedback
* Integrate with mobile apps for notifications
* Use internal RTC (ESP32 + NTP) as a fallback when external RTC is missing

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Contributing

Pull requests are welcome! If you’d like to add features or fix bugs, please open an issue first to discuss the changes.

---

## Contact

Have suggestions or questions?

* Open an issue on GitHub
* Start a discussion in the repo

```

---

Let me know when you're ready to move on to the **Python logger script**, **wiring table**, or anything else.
```

