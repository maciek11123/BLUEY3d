# BLUEY3d

Browser toys built on a procedural rig engine (`rig_engine.js`) driven by
MediaPipe pose tracking. Three.js for rendering, no build step — plain ES
modules loaded straight from the HTML.

## Crew

`Crew/crew.html` — all four characters on screen at once, each dancing its own
dance and reacting independently to your movement (wave, cheer, or just move
around and they'll join in). Music player, starfield, floating notes, and a
phone remote.

## Running it

The apps need to be served over HTTP (ES modules and `fetch` don't work from
`file://`):

```bash
py remote_server.py 8937
```

Then open <http://localhost:8937/Crew/crew.html>.

`remote_server.py` is a plain static file server plus a small in-memory command
relay, so a phone on the same Wi-Fi can drive the display. It prints both URLs
on startup.

## Phone remote

Open the `remote:` URL shown in the top-right of the display (something like
`http://192.168.0.22:8937/Crew/remote.html`) on a phone connected to the same
network. It can switch characters, control music and trigger reactions.

**The remote only works under `remote_server.py`.** On a static host (GitHub
Pages included) there is no relay, so the display detects that and silently
runs without it — everything else still works.

## Music

Drop `.mp3` files into `Music/`. They're picked up automatically on any server
that lists directories; `FALLBACK_TRACKS` in `Crew/crew.html` is the hardcoded
list used when the host doesn't.

The music player also drives the visuals — low-end energy pulses each character
and spawns floating notes.

## Credits

Bluey, Bingo, Kuromi and Pompompurin are the property of their respective
rights holders. This is a personal, non-commercial fan project.
