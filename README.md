# MarstekVenusHASteering
⚡ Battery Power Distribution Blueprint for Home Assistant

This blueprint manages dual battery systems with solar integration in Home Assistant. It dynamically charges or discharges batteries based on solar production and household power consumption, ensuring balanced SoC (State of Charge) and controlled energy flow.

📦 Features

Distributes solar surplus to two batteries while maintaining SoC balance.
Minimizes grid power usage by discharging batteries intelligently.
Limits rapid switching via a 60-second cooldown and 10-second update interval.
Fully configurable through UI (entities for SoC, power meter, power controls, etc.).
Blueprint structure enables reuse across different systems.
Optional logging using persistent_notification.
📁 Installation

Save the Blueprint File
Download or copy the blueprint YAML file (e.g., battery_power_manager.yaml) into your Home Assistant config/blueprints/automation/[your-username]/ directory.
Example path:

config/blueprints/automation/myuser/battery_power_manager.yaml
Restart Home Assistant (or reload automations via Developer Tools) to detect the new blueprint.
⚙️ Setup Automation

Go to Settings → Automations & Scenes → Automations.
Click “+ Add Automation” → “Start with a blueprint”.
Select Battery Power Distribution Blueprint.
Fill in all required entities:
Power meter sensor (must provide net power, negative for export).
SoC sensors for battery 1 and 2.
Charge/discharge power number entities for both batteries.
Mode select entities for both batteries.
Input helpers (text and datetime) to track mode and cooldown logic.
📝 Required Entities


Type	Description
sensor	sensor.power_meter – Net grid power (W)
sensor	sensor.battery_1_soc, sensor.battery_2_soc
number	Battery charge/discharge power controls
select	Battery mode selectors (charge, discharge, stop)
input_text	Helper to store system mode (charge, discharge, stop)
input_datetime	Helper to track last mode switch timestamp
✅ Tips

SoC values must be numerical percentages (0–100).
Net power meter must be negative when exporting power (solar > consumption).
Use input_text and input_datetime helpers to manage system mode and cooldown.
Monitor notifications in Home Assistant for debug logs.
