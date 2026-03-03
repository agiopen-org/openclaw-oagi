# OAGI Computer Use — OpenClaw Plugin

Desktop automation via the [OAGI Lux](https://developer.agiopen.org) computer-use model.

## Install

```bash
openclaw plugins install @oagi/openclaw-computer-use
```

## Prerequisites

- **API Key**: Get one at <https://developer.agiopen.org>. Set via `OAGI_API_KEY` env var or plugin config.
- **macOS**: Grant Accessibility permission to your terminal (System Settings > Privacy & Security > Accessibility).
- **Linux**: Install X11 dev headers (`sudo apt install libx11-dev libxtst-dev`).

## Native Dependencies

This plugin uses `robotjs` and `sharp` (via `@oagi/oagi`) for screen capture and input simulation. These are native modules that must be compiled for your platform.

OpenClaw's plugin installer skips build scripts (`--ignore-scripts`) for security. If `robotjs` fails to load at runtime, build it manually:

```bash
# Find the robotjs directory
find ~/.openclaw/extensions/oagi-computer-use -name "robotjs" -type d -path "*/node_modules/*"

# Build it
cd <path-from-above>
npx node-gyp rebuild
```

## Configuration

| Key           | Default                   | Description                   |
| ------------- | ------------------------- | ----------------------------- |
| `apiKey`      | `$OAGI_API_KEY`           | OAGI API key                  |
| `baseUrl`     | `https://api.agiopen.org` | API base URL                  |
| `model`       | `lux-actor-1`             | Model ID                      |
| `maxSteps`    | `20`                      | Max steps per task            |
| `temperature` | `0.5`                     | Sampling temperature          |
| `stepDelay`   | `1.0`                     | Delay between steps (seconds) |

## Development

Clone and install for local development:

```bash
git clone https://github.com/agiopen-org/openclaw-oagi.git
cd openclaw-oagi
npm install
```

Then load as a local extension in OpenClaw by adding the path to `plugins.load.paths` in your OpenClaw config.

## License

MIT
