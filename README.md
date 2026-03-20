# Atlas Monorepo

Monorepo setup for analytics SDK and example applications using npm workspaces.

## Structure

```
atlas/
├── analytics-js-sdk/       # Core SDK package
├── example/
│   └── my-analytics-test/  # Next.js example app
└── package.json            # Root workspace config
```

## Getting Started

### Install Dependencies

From the **root** directory:

```bash
npm install
```

This installs dependencies for all workspaces.

## Development

### Develop SDK with Live Reload

```bash
# From root
npm run dev:sdk
```

This watches the SDK source files and rebuilds automatically on changes.

### Run Example App

In a **separate terminal**:

```bash
# From root
npm run dev:example
```

Or manually:

```bash
cd example/my-analytics-test
npm run dev
```

### Develop Both Simultaneously

Run both commands in separate terminals:

```bash
# Terminal 1
npm run dev:sdk

# Terminal 2
npm run dev:example
```

Changes to the SDK will be automatically picked up by the Next.js app.

## Building

### Build SDK Only

```bash
npm run build:sdk
```

### Build Everything

```bash
npm run build:all
```

This builds the SDK first, then all example projects.

## How It Works

- **npm workspaces** link `analytics-js-sdk` to example projects
- The SDK dependency is specified as `"analytics-js-sdk": "*"` in example projects
- Next.js is configured with `transpilePackages: ['analytics-js-sdk']` to handle the workspace package
- Changes to SDK source are reflected after rebuild (automatic with `dev:sdk`)

## Adding New Examples

1. Create a new project in `example/` directory
2. Add `"analytics-js-sdk": "*"` to its dependencies
3. The workspace setup will automatically link it

## Troubleshooting

- **Module not found**: Make sure you ran `npm install` from the root
- **Changes not reflected**: Rebuild the SDK with `npm run build:sdk` or use `npm run dev:sdk` for watch mode
- **Turbopack errors**: Ensure `transpilePackages: ['analytics-js-sdk']` is in `next.config.ts`
# atlas-workspace
