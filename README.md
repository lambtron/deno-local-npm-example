# Local npm packages with Deno

This is an example of how to use local npm packages with Deno.

Deno 2.3 adds support for using a local npm package, making testing and
developing an npm package locally possible.

To use local npm modules, you’ll need a local `node_modules` folder, which you
can achieve with either `"nodeModulesDir": "auto"` or
`"nodeModulesDir": "manual"`. (If you choose the latter, you will need to run
`deno install` each time you update your local npm package.)

Add the path to the directory of your local npm package in `deno.json` under
`patch`:

```json
{
  "patch": [
    "../path/to/local_npm_package"
  ]
}
```

Finally, if you selected `"nodeModulesDir": "manual"`, then run `deno install`.

Note that, at the moment, your local npm package name must also exist in the npm
registry.

Please refer to [Deno 2.3](https://deno.com/blog/v2.3) for more information.
