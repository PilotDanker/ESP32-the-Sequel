# ESP32-the-Sequel
This is a Hardware-in-the-Loop (HIL) robot simulation using **Webots** and an **ESP32** microcontroller. It’s designed to showcase real-time robot control over WiFi using a Dijkstra-based pathfinding system. The robot follows a line in simulation and makes decisions live using data from Webots and commands from the ESP32.

---

## 🎯 What It Does

- Webots simulates the environment and robot sensors.
- ESP32 receives data (position, line sensors), calculates the path, and sends back commands (`"forward"`, `"turn_left"`, etc).
- Everything runs over TCP using simple JSON messages.
- The robot follows a black line, avoids white space, and replans if needed.

---

## 🧠 Key Features

- Line-following with IR sensor array
- Dijkstra path planning on ESP32 (MicroPython)
- Real-time WiFi communication using sockets
- Webots controller in Python
- Optional matplotlib visualization (live plotting)

---

## 📁 Folder Structure

ESP32-the-Sequel/
├── controllers/
│   └── the_sequel_bot.py       # Webots controller script
├── esp32_code/
│   └── Dijkstra.py             # ESP32-side algorithm (MicroPython)
├── world/
│   ├── RaFLite.wbt             # Webots world
│   └── textures/
│       └── RaFLite_track.png   # Floor texture
├── .gitignore
└── README.md

---

## 🔌 Communication

|    Direction   |         Data Type        |
|----------------|--------------------------|
| Webots → ESP32 | Grid position, IR sensor |
| ESP32 → Webots | Movement command         |

All messages are in **JSON** format, sent over **TCP** (port `8080`).

---

## 🛠️ Tools Used

- Webots R2025a
- ESP32 (MicroPython, Thonny IDE)
- Python (sockets, json, matplotlib)
- Dijkstra pathfinding

---

## 📚 Project Info

Made for a university project focused on embedded systems and robotics.  
Specialization: Mechatronics  
Team Name: *Robot Group*  
Controller Name: `the_sequel_bot`

---

## ⚠️ Notes

- No license applied — for educational use only.
- You may need to adjust IP addresses depending on your local network setup.
- Matplotlib plots are optional and can be disabled if running headless.

---

## 💬 Final Thoughts

> The first robot walked.  
> **This one calculates.**  
>  
> *ESP32-the-Sequel* — now with 100% more pathfinding and WiFi drama.
