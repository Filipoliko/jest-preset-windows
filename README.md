# Jest preset via exports on Windows

Jest preset fails to be recognized on Windows when the preset module is defining `jest-preset.js` via `exports` in `package.json`.

Linux and MacOS are not affected by this issue.

## Steps to reproduce

1. Clone this repository
2. Run `npm ci`
3. Run `npm test`

## Expected behavior

Jest should run the test suite without any issues.

## Actual behavior (Windows)

Test fails to find the preset module.

## Repository structure

Our fake preset module is defined in `packages/my-jest-preset` and installed via `workspaces` in the root `package.json`.

The preset is defining global variable `__DEV__` to `true`.

The root `jest.config.js` file is using the preset.

The `dummy.test.js` file is simply checking if `__DEV__` is defined.
