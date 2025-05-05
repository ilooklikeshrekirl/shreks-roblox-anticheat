# 🛡️ Roblox Anti-Cheat Script

A simple server-side anti-cheat system for Roblox games that detects common exploit attempts like speed hacks, teleporting, and RemoteEvent abuse.

---

## 📂 Features

- ✅ Detects and kicks for:
  - WalkSpeed exploits
  - JumpPower exploits
  - Sudden teleporting (server-side distance checks)
  - RemoteEvent misuse (invalid data types)
- 🔒 Server-sided for better security
- 💬 Easy to extend with your own checks

---

## 📦 Installation

1. Open your Roblox game in **Roblox Studio**.
2. Insert a **Script** inside **`ServerScriptService`**.
3. Copy and paste the contents of **`AntiCheat.lua`** from this repo into the script.
4. Add a **RemoteEvent** in **`ReplicatedStorage`** and name it **`SecureEvent`**.

---

## 🧪 Testing

#### Simulate Speed Hack:
Open the **Command Bar** while playing in Studio:

```lua
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 100
This will simulate a speed hack. The anti-cheat should kick the player because 100 is above the allowed MAX_WALK_SPEED (20).

Simulate Teleport Exploit:
In the Command Bar, run:

lua
Copy
Edit
game.Players.LocalPlayer.Character:MoveTo(Vector3.new(999, 100, 999))
This will teleport the player to a far location. The anti-cheat will kick the player for teleporting more than the allowed MAX_DISTANCE (50 studs).

Simulate RemoteEvent Abuse:
In the Command Bar, run:

lua
Copy
Edit
game.ReplicatedStorage.SecureEvent:FireServer({})
This sends invalid data ({}) to the server. The anti-cheat will detect the malformed data and kick the player.

📜 How It Works
Movement Monitoring:

The script listens for changes to the player's WalkSpeed and JumpPower. If a player exceeds the specified limits, they will be kicked.

Teleport Detection:

The script compares the player's last position to their current position, and if they move too far too quickly (more than the MAX_DISTANCE), it kicks the player for teleporting.

RemoteEvent Validation:

It checks the type of data sent via the SecureEvent RemoteEvent. If the data is malformed (e.g., sending a table when a string is expected), the player is kicked.

🚧 Future Improvements (Optional)
 Anti-Noclip Logic: Detect if the player is walking through walls or objects (simulating noclip).

 Warnings Before Kicking: Instead of kicking the player instantly, you could send a warning message first.

 Admin Bypass: Allow admins to bypass anti-cheat restrictions.

 Remote Spam Cooldowns: Limit how often players can fire RemoteEvents to prevent abuse.

📄 License
This project is free to use and modify. Credit is appreciated, but not required.

pgsql
Copy
Edit
