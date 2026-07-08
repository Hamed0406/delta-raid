# Delta Raid

A colorful single-file HTML game inspired by the 1982 Atari classic *River Raid*.

- **Zero dependencies** — no npm, no build step, no assets, no Docker
- Canvas graphics, WebAudio sound, procedurally generated river
- Levels, fuel management, high score saved in your browser

## How to run

### Option 1 — you have a desktop/laptop: just open the file

Copy `index.html` anywhere and open it in any modern browser
(double-click it, or drag it into a browser window). That's it.

```bash
# e.g. copy it from the server to your own machine first:
scp user@192.168.1.212:/opt/River-Raid/index.html .
```

### Option 2 — hosting on a headless Linux server

Serve the folder with Python's built-in web server (already installed on
virtually every Linux box):

```bash
cd /opt/River-Raid
python3 -m http.server 8000
```

Then open `http://<server-ip>:8000` in a browser on any device on the
same network.

If the port is blocked by a firewall, tunnel it over SSH from your own
machine instead:

```bash
ssh -L 8000:localhost:8000 user@<server-ip>
# then open http://localhost:8000
```

To stop the server: `Ctrl-C` (or `pkill -f "http.server 8000"` if it runs
in the background).

## How to play

Press **Enter**, click, or tap to start.

**Keyboard:**

| Key | Action |
|---|---|
| ← → or A D | Steer left / right |
| ↑ or W | Throttle up (faster, burns more fuel) |
| ↓ or S | Brake |
| Space | Shoot |
| P | Pause |
| M | Mute |
| Enter | Start / restart |

**Touch (phone / tablet):** drag your finger — the plane follows its
left/right position and fires automatically. Only the horizontal position
matters, so rest your finger wherever it doesn't block your view (e.g.
below the plane). Hold in the top third of the screen to throttle up;
hold on the bottom HUD bar to brake.

### Rules

- Stay over the water — touching the banks, islands, or anything else crashes you.
- **Fuel** drains constantly (faster at full throttle). Fly over the red
  **F** depots to refuel — or shoot them for points if your tank is comfortable.
- **Shoot the bridges** to advance to the next level. Each level is faster,
  narrower, and busier.
- You have 3 lives. After each death you get a brief blinking grace period.

| Target | Points |
|---|---|
| Ship | 30 |
| Helicopter | 60 |
| Jet | 100 |
| Fuel depot | 80 |
| Bridge | 500 (+ next level) |

High score is saved automatically in your browser.

## Project layout

```
index.html   the entire game (~500 lines, HTML + CSS + JS inline)
PLAN.md      design notes, architecture, build history, backlog
README.md    this file
```

For how the game works internally (coordinate system, procedural river,
difficulty dials) and the engineering principles behind it, see
[PLAN.md](PLAN.md).
