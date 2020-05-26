# Runner

![Runner](https://cloud.githubusercontent.com/assets/1157043/17947042/e9352ae2-6a18-11e6-85af-3670c7cfba03.png)

The runner is the minimal "chrome" around the user's app and has the following responsibilities:

- Managing communication between the driver, the reporter, the extension, and the server
- Managing the viewport size and scale
- Showing the currently active URL

## Developing

### Watching

This watches and compiles all changes as you make them.

- Runs `*.js` and `*.jsx` through babel and bundles with browserify into single `dist/cypress_runner.js`
- Runs associated unit test of file saved and outputs to terminal
- Compiles `*.scss` files to single `dist/cypress_runner.css`
- Additionally it compiles both the [`reporter`](../reporter) and [`driver`](../driver)

```bash
yarn lerna run watch --scope @packages/runner --stream
```

## Building

### For development

```bash
yarn lerna run build --scope @packages/runner --stream
```

### For production

```bash
yarn lerna run build-prod --scope @packages/runner --stream
```

## Testing

### Node Unit Tests

```bash
yarn lerna run test --scope @packages/runner --stream
```

### Cypress

You'll need to start the server from the [`driver`](../driver) package in order to get Cypress running.

```bash
yarn lerna run start --scope @packages/driver --stream
```

Then you can run Cypress tests found in [`test/cypress/integration`](./test/cypress/integration).

```bash
yarn lerna run cypress:open --scope @packages/runner --stream
```

To see changes to the reporter while testing you'll want to run:

```bash
yarn lerna run watch --scope @packages/runner --stream
```