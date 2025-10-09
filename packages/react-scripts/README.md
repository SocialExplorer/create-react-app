# react-scripts

---

This fork includes the following changes:

1. **New Webpack Configuration:**

   - Introduces 2 webpack configurations with a different entry point: `src/widget.js`.
   - Aims to output a single JavaScript file.
   - Outputs everything to `/widget` and `/widget-umd` by default.
   - The news webpack configurations accepts the following environment variables:
     - `WIDGET_PUBLIC_URL` (similar to `PUBLIC_URL`): Defaults to `"/widget/"`.
     - `WIDGET_BUILD_PATH` (similar to `BUILD_PATH`): Defaults to `"build/widget"`.
     - `WIDGET_UMD_PUBLIC_URL` (similar to `PUBLIC_URL`): Defaults to `"/widget-umd/"`.
     - `WIDGET_UMD_BUILD_PATH` (similar to `BUILD_PATH`): Defaults to `"build/widget-umd"`.
   - There are 2 new outputs, SystemJS named after the `name` field in the project's `package.json` file when using CRA and UMD named `LAYOUT`.

2. **Development Mode Enhancements:**

   - Dev server has CORS enabled
   - You can pass 2 new arguments `--widget` and `--widget-umd` to the `start` script in development mode.
     - When the `--widget` argument is passed, `webpack-dev-server` uses a new webpack configuration that outputs SystemJS.
     - When the `--widget-umd` argument is passed, `webpack-dev-server` uses a new webpack configuration that outputs UMD.
   - `webpack-dev-server` accepts the following environment variable:
     - `WIDGET_PORT` (similar to `PORT`): Defaults to `3210`.
     - `WIDGET_UMD_PORT` (similar to `PORT`): Defaults to `3220`.

3. **Proxying Requests in Development Mode:**
   - In development mode, all requests to `/widget/**/*` are proxied to the `/widget/**/*` path of the `webpack-dev-server` instance running with the `--widget` argument.
   - In development mode, all requests to `/widget-umd/**/*` are proxied to the `/widget-umd/**/*` path of the `webpack-dev-server` instance running with the `--widget-umd` argument.

### Steps to test locally

```
# in this directory, run
$ yarn link

# in `viz-omni/frontend-neo/layout-editor`
$ yarn link se-cra-react-scripts
```

### Steps to publish to npm

1. Update package.json version
1. Run:

   ```
   $ npm login
   # update package.json version
   $ npm publish
   ```

### Troubleshooting

- [Uncaught ReferenceError: process is not defined](https://github.com/facebook/create-react-app/issues/12374)

  Latest versions of `react-error-overlay` have that bug. Add the following to your `package.json` to fix it:

  ```json
  "resolutions": {
    "react-error-overlay": "6.0.8"
  },
  ```

---

This package includes scripts and configuration used by [Create React App](https://github.com/facebook/create-react-app).<br>
Please refer to its documentation:

- [Getting Started](https://facebook.github.io/create-react-app/docs/getting-started) – How to create a new app.
- [User Guide](https://facebook.github.io/create-react-app/) – How to develop apps bootstrapped with Create React App.
