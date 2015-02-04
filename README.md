# node-typescript-seed

I couldn't find a good seed for a Node+TypeScript workflow, so I made my own.

This is set up for a client/server app.  A basic static content server using
`express` is provided.  The client bundle has correct source maps pointing to
the original TypeScript code.  It's currently a bit rough, but it works.

## Project layout:

* `src/` - Typescript source goes here.
* `src/client/index.ts` - Client-side entry point.
* `src/server/index.ts` - Server-side entry point.
* `src/common/` - Source files common to both client and server.
* `lib/` - Compiled server-side code.
* `www/` - Web root.  Compiled client-side code is saved to `client.js`.

To compile for production (minified client file): `gulp build-all`

For development (reloads on code change): `gulp watch`

Getting this to work was a bit of an ordeal.  Currently completely different
workflows are used for the client and server due to the limitations of
existing TS-compatible toolsets.  This means that the compiler version may
not necessarily be consistent if you blindly update the modules.
Currently, both workflows use TypeScript compiler v1.4.1.

This could be greatly simplified if both builds could use Browserify, but
this seems to be problematic (bare bundles don't seem to work properly).
Any help would be appreciated!
