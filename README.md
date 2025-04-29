# Local npm packages with Deno

Deno 2.3 adds support for using a local npm package, making testing and
developing an npm package locally possible.

This is an example of how to use local npm packages with Deno.
[Please refer to accompanying Deno 2.3 release notes.](https://deno.com/blog/v2.3)

## Requirements

To use local npm modules, you’ll need a local `node_modules` folder, which you
can achieve with either `"nodeModulesDir": "auto"` or
`"nodeModulesDir": "manual"`. (If you choose the latter, you will need to run
`deno install` each time you update your local npm package.)

## Setup

### 1. Add path to local npm package

Add the path to the directory of your local npm package in `deno.json` under
`patch`:

```json
{
  "patch": [
    "../path/to/local/chalk"
  ]
}
```

Note that, at the moment, your local npm package name must also exist in the npm
registry.

### 2. Install dependencies

This will install the `chalk` package from npm into your local npm directory as
specified by your path.

```bash
$ deno install
```

### 3. Modify your package locally

We'll make a small change and add the following line to the first function at
the top of `index.js`:

```diff
  function Chalk(options) {
+     console.log("Hello, world from local Chalk!");

      // detect mode if not set manually
      this.enabled = !options || options.enabled === undefined
          ? supportsColor
          : options.enabled;
}
```

### 4. Run your program

Finally, when you run `main.ts` you will see the updated local Chalk package.

```bash
$ deno -A main.ts
Hello, world from local Chalk!
Hello
```

Please refer to [Deno 2.3](https://deno.com/blog/v2.3) for more information.
