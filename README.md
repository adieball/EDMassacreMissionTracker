# 🛰️ Elite Dangerous Massacre Mission Tracker

A real-time tool that tracks **massacre missions** in **Elite Dangerous**, posting updates to **Discord** and displaying mission progress on a sleek local **web dashboard**.

Supports:
- Multiple game clients (e.g. alt accounts)
- Multiple commanders (auto-detected)
- Persistent tracking across restarts
- Kill rate per hour calculation
- Progress bars and mission summaries

---

## 🔧 Features

- 📥 Automatically detects accepted massacre missions
- 💀 Tracks every kill (via `Bounty` journal events)
- ✅ Sends real-time updates via **Discord Webhook**
- 🌐 Hosts a **dashboard** at `http://<your-ip>:5000`
- 🎨 Clean, color-coded UI with mission providers, names, and progress bars
- 📊 Kill rate per hour
- 🔁 Auto-refresh every 10 seconds
- 🧠 Remembers progress even after restarting the script or Elite

---

## 📸 Dashboard Preview

```
📊 Massacre Mission Tracker
CMDR: f0rd42

🧮 Total Progress: 38/72 kills (52%)
⏱️ Kill Rate: 22.1 kills/hour

• [Aegis Defense] Massacre 72 Thargoids: 38/72
• [Pilots Federation] Massacre 8 Scouts: 4/8
```

---

## 📦 Installation

### 1. Prerequisites

- Python 3.9 or newer
- Elite Dangerous installed (Steam/Frontier/EDO)
- Journal logging enabled (default setting)

### 2. Clone this repo

```bash
git clone https://github.com/yourusername/massacre-tracker.git
cd massacre-tracker
```

### 3. Install Python requirements

```bash
pip install flask requests
```

### 4. Configure Discord Webhook (optional)

Open `massacre_tracker.py` and set:

```python
USE_DISCORD = True  # Set to False to disable Discord messages
WEBHOOK_URL = "https://discord.com/api/webhooks/your_webhook_here"
```

---

## ▶️ Running the Tracker

Run the tracker with:

```bash
python massacre_tracker.py
```

- Dashboard will be available at: `http://<your-ip>:5000`
- Discord messages will be posted automatically (if enabled)

---

## ⚙️ Configuration Options

All settings are inside `massacre_tracker.py`:

```python
USE_DISCORD = True         # Enable or disable Discord webhook posting
USE_DASHBOARD = True       # Enable or disable web dashboard
DASHBOARD_PORT = 5000      # Web dashboard port
SUMMARY_INTERVAL = 300     # Discord summary interval (seconds)
```

---

## 🧪 Example Discord Output

```
📥 Accepted Massacre 72 Thargoids for Aegis Defense — need to kill 72.
💀 Kill for Massacre 72 Thargoids (1/72)
💀 Kill for Massacre 72 Thargoids (2/72)
...
✅ Completed Massacre 72 Thargoids — 72/72 kills.
```

---

## 🌐 Local Web Access

Once running, you can access the dashboard from any device in your network:

```
http://<your-computer-ip>:5000
```

Find your IP address with:

```bash
ipconfig   # on Windows
ifconfig   # on Linux/macOS
```

---

## 🗃️ Persistent Tracking

Your massacre mission progress is saved to:

```
./mission_state.json
```

You can stop and restart the script or the game, and all progress will be restored.

---

## 🧠 Internals / Events Tracked

This tracker parses the following Elite Dangerous journal events:

| Event           | Purpose                     |
|-----------------|-----------------------------|
| `LoadGame`      | Detect commander name(s)    |
| `MissionAccepted` | Start tracking missions     |
| `Bounty`        | Count each kill             |
| `MissionCompleted` | Mark mission complete      |
| `MissionFailed` | Mark mission failed         |

---

## 🛡️ Security

- Runs **locally** on your machine (Flask server bound to `0.0.0.0`)
- Accessible only on your local network unless port-forwarded manually
- Password protection not included (yet)

---

## 🗂️ Project Structure

```
massacre_tracker.py     # Main script
mission_state.json      # Auto-saved progress
README.md               # This file
```

---

## 🚀 Future Ideas

- [ ] CSV/JSON export
- [ ] Tray icon / background app version
- [ ] Dashboard password protection
- [ ] Alt-tab overlay (e.g. via Overwolf)
- [ ] Remote access deployment (Raspberry Pi, VPS)

---

## ❤️ Credits

Inspired by OD Elite Tracker and built with ❤️ for the Elite Dangerous community — especially Fuel Rats, AXI, and everyone grinding massacre missions into the void.

> Fly safe, CMDR o7

---

## 📜 License

This project is licensed under the MIT License.
