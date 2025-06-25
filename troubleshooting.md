# 🛠️ Troubleshooting – ESP32-the-Sequel

Things don’t always go smooth. If your robot isn’t moving, Webots is being dramatic, or your ESP32 is silent — this file is here to help.

---

### 🤖 The robot isn’t moving in Webots

- Make sure the controller in your `.wbt` file is set to `"the_sequel_bot"`.
- Confirm `the_sequel_bot.py` is inside the `/controllers/` folder.
- Start your ESP32 (`Dijkstra.py`) **before** pressing play in Webots.
- ESP32 and PC must be on the same WiFi network — check the IP!

---

### 🌐 “Connection reset by peer” or no response?

- This means Webots tried to connect to the ESP32, but it failed.
- Double-check the IP address at the top of `the_sequel_bot.py`.
- Restart both Webots and the ESP32 — works more often than it should.
- If the ESP32 crashed, re-upload the script or reboot it.

---

### 🧠 Robot is moving, but it’s not doing what it should

- Is it starting **on** the black line? It has to.
- The grid must be consistent:
  - `0` = black line (pathable)  
  - `1` = white area (obstacle)
- The robot will try to recover if it loses the line — spinning is normal.
- Line sensors might need tuning — check `LINE_THRESHOLD` in the code if needed.

---

### 🖥️ ESP32 doesn’t show up in Thonny

- Go to **Tools > Interpreter > MicroPython (ESP32)**
- Use a data USB cable (not just a charging cable).
- Try “Stop/Restart backend” in Thonny if things freeze.
- If all else fails, unplug and plug it back in.

---

### 📡 Webots isn’t getting commands from ESP32

- Make sure ESP32 is running and listening on port `8080`.
- Messages must end with `\n` — already handled in code, but worth checking.
- Watch the Webots terminal — you’ll see `"ESP32 Command:"` when data is received.

---

### 🗂️ Important: Don’t Save the World While It’s Running

Webots might ask you to save the world while you’re editing controllers or running simulations.

**⚠️ Don’t save it if the robot has already moved.**

Saving at that point can:
- Break the robot’s spawn position
- Lock in weird states
- Corrupt the `.wbt` file

**💡 Fix:**  
Keep a backup of your world file, like `RaFLite_backup.wbt`. If things break:
1. Delete the broken `RaFLite.wbt`
2. Copy the backup and rename it

> TL;DR – **Don’t save the world unless you mean it.**

---

### 🌐 Setting Up WiFi and IP Address (ESP32 Side)

Before the ESP32 can communicate with Webots, you’ll need to configure a few things.

1. **Your WiFi Name & Password**  
   In `Dijkstra.py` (ESP32), replace:

   ```python
   ssid = "YOUR_WIFI_NAME"
   password = "YOUR_WIFI_PASSWORD"
   Finding the ESP32’s IP Address
After booting, the ESP32 prints its IP in the Thonny serial monitor:

2. Finding the ESP32’s IP Address
   After booting, the ESP32 prints its IP in the Thonny serial monitor:

    Connected to WiFi
    IP address: xxx.xxx.x.xxx

    Copy that IP into the_sequel_bot.py:
    ESP32_IP_ADDRESS = "192.168.0.112"
   
4. Changing the Port (Optional)
The default is 8080. You can change it in both files — just make sure they match.

ESP32_PORT = 8080

If Webots can’t connect, 90% of the time it’s an IP or port mismatch.

🧹 Still broken?
Restart Webots and the ESP32

Check your network connection

Read the console output — it usually tells you what’s wrong

Take a break. Seriously. It helps.

This guide is just here to keep your sanity intact.
The robot wants to work — it just needs a little patience (and maybe a reboot).
