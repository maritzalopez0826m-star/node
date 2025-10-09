# Node.js 25 ChangeLog

<!--lint disable maximum-line-length no-literal-urls prohibited-strings-->

<table>
<tr>
<th>Current</th>
</tr>
<tr>
<td>
<a href="#25.0.0">25.0.0</a><br/>
</td>
</tr>
</table>

* Other Versions
  * [24.x](CHANGELOG_V24.md)
  * [23.x](CHANGELOG_V23.md)
  * [22.x](CHANGELOG_V22.md)
  * [21.x](CHANGELOG_V21.md)
  * [20.x](CHANGELOG_V20.md)
  * [19.x](CHANGELOG_V19.md)
  * [18.x](CHANGELOG_V18.md)
  * [17.x](CHANGELOG_V17.md)
  * [16.x](CHANGELOG_V16.md)
  * [15.x](CHANGELOG_V15.md)
  * [14.x](CHANGELOG_V14.md)
  * [13.x](CHANGELOG_V13.md)
  * [12.x](CHANGELOG_V12.md)
  * [11.x](CHANGELOG_V11.md)
  * [10.x](CHANGELOG_V10.md)
  * [9.x](CHANGELOG_V9.md)
  * [8.x](CHANGELOG_V8.md)
  * [7.x](CHANGELOG_V7.md)
  * [6.x](CHANGELOG_V6.md)
  * [5.x](CHANGELOG_V5.md)
  * [4.x](CHANGELOG_V4.md)
  * [0.12.x](CHANGELOG_V012.md)
  * [0.10.x](CHANGELOG_V010.md)
  * [io.js](CHANGELOG_IOJS.md)
  * [Archive](CHANGELOG_ARCHIVE.md)

<a id="25.0.0"></a>

## 2025-10-15, Version 25.0.0 (Current), @RafaelGSS

Node.js 25 is here! We have upgraded V8 to **14.1**, bringing major `JSON.stringify`
performance improvements, built-in `Uint8Array` base64/hex conversion, and ongoing
WebAssembly and JIT pipeline optimizations.

This release doubles down on secure-by-default apps and web-standard APIs: the permission
model gains `--allow-net`, Web Storage is enabled by default, and `ErrorEvent` is now a global.

We’ve also removed or finalized long-deprecated APIs, upgraded to a newer V8, and added quality-of-life
improvements like a portable compile cache and JSPI for WebAssembly.

### Notable Changes

* \[[`a472745958`](https://github.com/nodejs/node/commit/a472745958)] - **(SEMVER-MAJOR)** **crypto**: runtime-deprecate default shake128/256 output lengths (Filip Skokan) [#59008](https://github.com/nodejs/node/pull/59008)
* \[[`663554abdf`](https://github.com/nodejs/node/commit/663554abdf)] - **(SEMVER-MAJOR)** **lib**: expose global ErrorEvent (Richie Bendall) [#58920](https://github.com/nodejs/node/pull/58920)
* \[[`3312e4e946`](https://github.com/nodejs/node/commit/3312e4e946)] - **(SEMVER-MAJOR)** **src**: unflag --experimental-webstorage by default (Daniel M Brasil) [#57666](https://github.com/nodejs/node/pull/57666)
* \[[`462c74181d`](https://github.com/nodejs/node/commit/462c74181d)] - **(SEMVER-MAJOR)** **src,permission**: add --allow-net permission (Rafael Gonzaga) [#58517](https://github.com/nodejs/node/pull/58517)

### Deprecations and Removals

* \[[`d33f4b539a`](https://github.com/nodejs/node/commit/d33f4b539a)] - **(SEMVER-MAJOR)** **assert**: move assert.fail with multiple arguments to eol (James M Snell) [#58532](https://github.com/nodejs/node/pull/58532)
* \[[`b21574d63b`](https://github.com/nodejs/node/commit/b21574d63b)] - **(SEMVER-MAJOR)** **assert**: move CallTracker to EOL (James M Snell) [#58006](https://github.com/nodejs/node/pull/58006)
* \[[`308b6bc6de`](https://github.com/nodejs/node/commit/308b6bc6de)] - **(SEMVER-MAJOR)** **async\_hooks**: move `asyncResource` property on bound function to EOL (James M Snell) [#58618](https://github.com/nodejs/node/pull/58618)
* \[[`daced4ab98`](https://github.com/nodejs/node/commit/daced4ab98)] - **(SEMVER-MAJOR)** **buffer**: move SlowBuffer to EOL (Filip Skokan) [#58220](https://github.com/nodejs/node/pull/58220)
* \[[`df16f0fd8d`](https://github.com/nodejs/node/commit/df16f0fd8d)] - **(SEMVER-MAJOR)** **child\_process**: move \_channel to end-of-life (James M Snell) [#58527](https://github.com/nodejs/node/pull/58527)
* \[[`a472745958`](https://github.com/nodejs/node/commit/a472745958)] - **(SEMVER-MAJOR)** **crypto**: runtime-deprecate default shake128/256 output lengths (Filip Skokan) [#59008](https://github.com/nodejs/node/pull/59008)
* \[[`c3b986853c`](https://github.com/nodejs/node/commit/c3b986853c)] - **(SEMVER-MAJOR)** **crypto**: move deprecated hash and mgf1Hash options to EOL (James M Snell) [#58706](https://github.com/nodejs/node/pull/58706)
* \[[`66632648ba`](https://github.com/nodejs/node/commit/66632648ba)] - **(SEMVER-MAJOR)** **crypto**: runtime deprecate ECDH.setPublicKey() (James M Snell) [#58620](https://github.com/nodejs/node/pull/58620)
* \[[`a5f9ca1f77`](https://github.com/nodejs/node/commit/a5f9ca1f77)] - **(SEMVER-MAJOR)** **dns**: move falsy hostname in lookup to end-of-life (James M Snell) [#58619](https://github.com/nodejs/node/pull/58619)
* \[[`2bb7667475`](https://github.com/nodejs/node/commit/2bb7667475)] - **(SEMVER-MAJOR)** **fs**: move FileHandle close on GC to EOL (James M Snell) [#58536](https://github.com/nodejs/node/pull/58536)
* \[[`eec0302088`](https://github.com/nodejs/node/commit/eec0302088)] - **(SEMVER-MAJOR)** **fs**: move rmdir recursive option to end-of-life (James M Snell) [#58616](https://github.com/nodejs/node/pull/58616)
* \[[`25dd206c29`](https://github.com/nodejs/node/commit/25dd206c29)] - **(SEMVER-MAJOR)** **fs**: remove `fs.F_OK`, `fs.R_OK`, `fs.W_OK`, `fs.X_OK` (Livia Medeiros) [#55862](https://github.com/nodejs/node/pull/55862)
* \[[`91dadf2897`](https://github.com/nodejs/node/commit/91dadf2897)] - **(SEMVER-MAJOR)** **http**: deprecate writeHeader (Sebastian Beltran) [#59060](https://github.com/nodejs/node/pull/59060)
* \[[`4e06a648ff`](https://github.com/nodejs/node/commit/4e06a648ff)] - **(SEMVER-MAJOR)** **perf\_hooks**: move deprecated accessors to EOF (James M Snell) [#58531](https://github.com/nodejs/node/pull/58531)
* \[[`a3dfca90d1`](https://github.com/nodejs/node/commit/a3dfca90d1)] - **(SEMVER-MAJOR)** **process**: move multipleResolves event to EOL (James M Snell) [#58707](https://github.com/nodejs/node/pull/58707)
* \[[`790acc8689`](https://github.com/nodejs/node/commit/790acc8689)] - **(SEMVER-MAJOR)** **tls**: move IP-address servername deprecation to eol (James M Snell) [#58533](https://github.com/nodejs/node/pull/58533)
* \[[`3aaa2ebe19`](https://github.com/nodejs/node/commit/3aaa2ebe19)] - **(SEMVER-MAJOR)** **url**: move bad port deprecation in legacy url to end-of-life (James M Snell) [#58617](https://github.com/nodejs/node/pull/58617)

### Semver-Major Commits

* \[[`d33f4b539a`](https://github.com/nodejs/node/commit/d33f4b539a)] - **(SEMVER-MAJOR)** **assert**: move assert.fail with multiple arguments to eol (James M Snell) [#58532](https://github.com/nodejs/node/pull/58532)
* \[[`b21574d63b`](https://github.com/nodejs/node/commit/b21574d63b)] - **(SEMVER-MAJOR)** **assert**: move CallTracker to EOL (James M Snell) [#58006](https://github.com/nodejs/node/pull/58006)
* \[[`7c9fbc15bc`](https://github.com/nodejs/node/commit/7c9fbc15bc)] - **(SEMVER-MAJOR)** **assert,util**: fail promise comparison in deep equal checks (Ruben Bridgewater) [#59448](https://github.com/nodejs/node/pull/59448)
* \[[`11222f1a27`](https://github.com/nodejs/node/commit/11222f1a27)] - **(SEMVER-MAJOR)** **assert,util**: handle invalid dates as equal in deep comparison (Ruben Bridgewater) [#57627](https://github.com/nodejs/node/pull/57627)
* \[[`308b6bc6de`](https://github.com/nodejs/node/commit/308b6bc6de)] - **(SEMVER-MAJOR)** **async\_hooks**: move `asyncResource` property on bound function to EOL (James M Snell) [#58618](https://github.com/nodejs/node/pull/58618)
* \[[`daced4ab98`](https://github.com/nodejs/node/commit/daced4ab98)] - **(SEMVER-MAJOR)** **buffer**: move SlowBuffer to EOL (Filip Skokan) [#58220](https://github.com/nodejs/node/pull/58220)
* \[[`8a87ba031b`](https://github.com/nodejs/node/commit/8a87ba031b)] - **(SEMVER-MAJOR)** **build**: bump minimum Clang version to 19 (Michaël Zasso) [#59048](https://github.com/nodejs/node/pull/59048)
* \[[`21b131e93a`](https://github.com/nodejs/node/commit/21b131e93a)] - **(SEMVER-MAJOR)** **build**: reset embedder string to "-node.0" (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`f31c88021b`](https://github.com/nodejs/node/commit/f31c88021b)] - **(SEMVER-MAJOR)** **build**: stop distributing Corepack (Antoine du Hamel) [#57617](https://github.com/nodejs/node/pull/57617)
* \[[`df16f0fd8d`](https://github.com/nodejs/node/commit/df16f0fd8d)] - **(SEMVER-MAJOR)** **child\_process**: move \_channel to end-of-life (James M Snell) [#58527](https://github.com/nodejs/node/pull/58527)
* \[[`a472745958`](https://github.com/nodejs/node/commit/a472745958)] - **(SEMVER-MAJOR)** **crypto**: runtime-deprecate default shake128/256 output lengths (Filip Skokan) [#59008](https://github.com/nodejs/node/pull/59008)
* \[[`c3b986853c`](https://github.com/nodejs/node/commit/c3b986853c)] - **(SEMVER-MAJOR)** **crypto**: move deprecated hash and mgf1Hash options to EOL (James M Snell) [#58706](https://github.com/nodejs/node/pull/58706)
* \[[`66632648ba`](https://github.com/nodejs/node/commit/66632648ba)] - **(SEMVER-MAJOR)** **crypto**: runtime deprecate ECDH.setPublicKey() (James M Snell) [#58620](https://github.com/nodejs/node/pull/58620)
* \[[`6d61175db0`](https://github.com/nodejs/node/commit/6d61175db0)] - **(SEMVER-MAJOR)** **deps**: V8: backport 1d3362c55396 (Shu-yu Guo) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`974773572e`](https://github.com/nodejs/node/commit/974773572e)] - **(SEMVER-MAJOR)** **deps**: V8: cherry-pick 4f38995c8295 (Shu-yu Guo) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`70bfc398e9`](https://github.com/nodejs/node/commit/70bfc398e9)] - **(SEMVER-MAJOR)** **deps**: V8: cherry-pick 044b9b6f589d (Rezvan Mahdavi Hezaveh) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`6bfc525cf0`](https://github.com/nodejs/node/commit/6bfc525cf0)] - **(SEMVER-MAJOR)** **deps**: V8: cherry-pick d2ad518a0b57 (Joyee Cheung) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`754d28e34f`](https://github.com/nodejs/node/commit/754d28e34f)] - **(SEMVER-MAJOR)** **deps**: V8: revert 6d6c1e680c7b (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`8c508b9399`](https://github.com/nodejs/node/commit/8c508b9399)] - **(SEMVER-MAJOR)** **deps**: V8: revert e3cddbedb205 (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`88ca8287b6`](https://github.com/nodejs/node/commit/88ca8287b6)] - **(SEMVER-MAJOR)** **deps**: use std::map in MSVC STL for EphemeronRememberedSet (Joyee Cheung) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`838e2332a5`](https://github.com/nodejs/node/commit/838e2332a5)] - **(SEMVER-MAJOR)** **deps**: patch V8 for illumos (Dan McDonald) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`3522731d9a`](https://github.com/nodejs/node/commit/3522731d9a)] - **(SEMVER-MAJOR)** **deps**: remove problematic comment from v8-internal (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`d234475a33`](https://github.com/nodejs/node/commit/d234475a33)] - **(SEMVER-MAJOR)** **deps**: define V8\_PRESERVE\_MOST as no-op on Windows (Stefan Stojanovic) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`a738eb4a7f`](https://github.com/nodejs/node/commit/a738eb4a7f)] - **(SEMVER-MAJOR)** **deps**: fix FP16 bitcasts.h (Stefan Stojanovic) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`1744c7d991`](https://github.com/nodejs/node/commit/1744c7d991)] - **(SEMVER-MAJOR)** **deps**: patch V8 to avoid duplicated zlib symbol (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`fff0d1554d`](https://github.com/nodejs/node/commit/fff0d1554d)] - **(SEMVER-MAJOR)** **deps**: update V8 to 13.7.152.9 (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`968e2f47c8`](https://github.com/nodejs/node/commit/968e2f47c8)] - **(SEMVER-MAJOR)** **dgram**: move deprecated APIs to EOL (James M Snell) [#58474](https://github.com/nodejs/node/pull/58474)
* \[[`a5f9ca1f77`](https://github.com/nodejs/node/commit/a5f9ca1f77)] - **(SEMVER-MAJOR)** **dns**: move falsy hostname in lookup to end-of-life (James M Snell) [#58619](https://github.com/nodejs/node/pull/58619)
* \[[`2bb7667475`](https://github.com/nodejs/node/commit/2bb7667475)] - **(SEMVER-MAJOR)** **fs**: move FileHandle close on GC to EOL (James M Snell) [#58536](https://github.com/nodejs/node/pull/58536)
* \[[`eec0302088`](https://github.com/nodejs/node/commit/eec0302088)] - **(SEMVER-MAJOR)** **fs**: move rmdir recursive option to end-of-life (James M Snell) [#58616](https://github.com/nodejs/node/pull/58616)
* \[[`823ca6991f`](https://github.com/nodejs/node/commit/823ca6991f)] - **(SEMVER-MAJOR)** **fs**: make `processReadResult()` and `readSyncRecursive()` private (Livia Medeiros) [#58672](https://github.com/nodejs/node/pull/58672)
* \[[`a273674dee`](https://github.com/nodejs/node/commit/a273674dee)] - **(SEMVER-MAJOR)** **fs**: move fs stream open method to eol (James M Snell) [#58529](https://github.com/nodejs/node/pull/58529)
* \[[`25dd206c29`](https://github.com/nodejs/node/commit/25dd206c29)] - **(SEMVER-MAJOR)** **fs**: remove `fs.F_OK`, `fs.R_OK`, `fs.W_OK`, `fs.X_OK` (Livia Medeiros) [#55862](https://github.com/nodejs/node/pull/55862)
* \[[`91dadf2897`](https://github.com/nodejs/node/commit/91dadf2897)] - **(SEMVER-MAJOR)** **http**: deprecate writeHeader (Sebastian Beltran) [#59060](https://github.com/nodejs/node/pull/59060)
* \[[`663554abdf`](https://github.com/nodejs/node/commit/663554abdf)] - **(SEMVER-MAJOR)** **lib**: expose global ErrorEvent (Richie Bendall) [#58920](https://github.com/nodejs/node/pull/58920)
* \[[`cd68e35704`](https://github.com/nodejs/node/commit/cd68e35704)] - **(SEMVER-MAJOR)** **lib**: deprecate `_stream_*` modules (Dario Piotrowicz) [#58337](https://github.com/nodejs/node/pull/58337)
* \[[`a822a1cbe7`](https://github.com/nodejs/node/commit/a822a1cbe7)] - **(SEMVER-MAJOR)** **lib**: deprecate \_tls\_common and \_tls\_wrap (Dario Piotrowicz) [#57643](https://github.com/nodejs/node/pull/57643)
* \[[`705bcc2a00`](https://github.com/nodejs/node/commit/705bcc2a00)] - **(SEMVER-MAJOR)** **module**: move Module.\_debug to end-of-life (James M Snell) [#58473](https://github.com/nodejs/node/pull/58473)
* \[[`5fe7800683`](https://github.com/nodejs/node/commit/5fe7800683)] - **(SEMVER-MAJOR)** **node-api**: add warning for NAPI\_EXPERIMENTAL (Miguel Marcondes Filho) [#58280](https://github.com/nodejs/node/pull/58280)
* \[[`4e06a648ff`](https://github.com/nodejs/node/commit/4e06a648ff)] - **(SEMVER-MAJOR)** **perf\_hooks**: move deprecated accessors to EOF (James M Snell) [#58531](https://github.com/nodejs/node/pull/58531)
* \[[`a3dfca90d1`](https://github.com/nodejs/node/commit/a3dfca90d1)] - **(SEMVER-MAJOR)** **process**: move multipleResolves event to EOL (James M Snell) [#58707](https://github.com/nodejs/node/pull/58707)
* \[[`e1d4d6ab49`](https://github.com/nodejs/node/commit/e1d4d6ab49)] - **(SEMVER-MAJOR)** **repl**: eol deprecate instantiating without new (Aviv Keller) [#59495](https://github.com/nodejs/node/pull/59495)
* \[[`234c26cca3`](https://github.com/nodejs/node/commit/234c26cca3)] - **(SEMVER-MAJOR)** **src**: store `Local` for `CallbackScope` on stack (Anna Henningsen) [#59705](https://github.com/nodejs/node/pull/59705)
* \[[`708fd1945b`](https://github.com/nodejs/node/commit/708fd1945b)] - **(SEMVER-MAJOR)** **src**: remove node.h APIs to make callback without an async context (Chengzhong Wu) [#58471](https://github.com/nodejs/node/pull/58471)
* \[[`56989d33f5`](https://github.com/nodejs/node/commit/56989d33f5)] - **(SEMVER-MAJOR)** **src**: remove deprecated node::EmitBeforeExit and node::EmitExit (Chengzhong Wu) [#58469](https://github.com/nodejs/node/pull/58469)
* \[[`d429aa2d17`](https://github.com/nodejs/node/commit/d429aa2d17)] - **(SEMVER-MAJOR)** **src**: remove deprecated node::CreatePlatform and node::FreePlatform (Chengzhong Wu) [#58470](https://github.com/nodejs/node/pull/58470)
* \[[`e0ae14ce73`](https://github.com/nodejs/node/commit/e0ae14ce73)] - **(SEMVER-MAJOR)** **src**: remove deprecated node::InitializeNodeWithArgs (Chengzhong Wu) [#58470](https://github.com/nodejs/node/pull/58470)
* \[[`db1700e4b5`](https://github.com/nodejs/node/commit/db1700e4b5)] - **(SEMVER-MAJOR)** **src**: update NODE\_MODULE\_VERSION to 138 (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`462c74181d`](https://github.com/nodejs/node/commit/462c74181d)] - **(SEMVER-MAJOR)** **src,permission**: add --allow-net permission (Rafael Gonzaga) [#58517](https://github.com/nodejs/node/pull/58517)
* \[[`790acc8689`](https://github.com/nodejs/node/commit/790acc8689)] - **(SEMVER-MAJOR)** **tls**: move IP-address servername deprecation to eol (James M Snell) [#58533](https://github.com/nodejs/node/pull/58533)
* \[[`a8217a9eb8`](https://github.com/nodejs/node/commit/a8217a9eb8)] - **(SEMVER-MAJOR)** **tools**: update V8 gypfiles for 13.7 (Michaël Zasso) [#58064](https://github.com/nodejs/node/pull/58064)
* \[[`3aaa2ebe19`](https://github.com/nodejs/node/commit/3aaa2ebe19)] - **(SEMVER-MAJOR)** **url**: move bad port deprecation in legacy url to end-of-life (James M Snell) [#58617](https://github.com/nodejs/node/pull/58617)
* \[[`fdef0725de`](https://github.com/nodejs/node/commit/fdef0725de)] - **(SEMVER-MAJOR)** **util,console**: colorize regexp groups, character classes, etc (Ruben Bridgewater) [#59710](https://github.com/nodejs/node/pull/59710)
* \[[`411cc42d22`](https://github.com/nodejs/node/commit/411cc42d22)] - **(SEMVER-MAJOR)** **worker**: move terminate callback to end-of-life (James M Snell) [#58528](https://github.com/nodejs/node/pull/58528)

### Semver-Minor Commits

* \[[`94422e8a40`](https://github.com/nodejs/node/commit/94422e8a40)] - **(SEMVER-MINOR)** **src**: add an option to make compile cache portable (Aditi) [#58797](https://github.com/nodejs/node/pull/58797)
* \[[`29738c7b42`](https://github.com/nodejs/node/commit/29738c7b42)] - **(SEMVER-MINOR)** **src,permission**: add --allow-inspector ability (Rafael Gonzaga) [#59711](https://github.com/nodejs/node/pull/59711)

### Semver-Patch Commits

* \[[`91f035e597`](https://github.com/nodejs/node/commit/91f035e597)] - **assert**: resolve TODO and rename function (Antoine du Hamel) [#59451](https://github.com/nodejs/node/pull/59451)
* \[[`22a864a275`](https://github.com/nodejs/node/commit/22a864a275)] - **build**: remove corepack from release tarballs (Jordan Harband) [#59835](https://github.com/nodejs/node/pull/59835)
* \[[`7079041e0a`](https://github.com/nodejs/node/commit/7079041e0a)] - **build**: only mention Apple when on Apple (Michaël Zasso) [#59385](https://github.com/nodejs/node/pull/59385)
* \[[`954d3f44ef`](https://github.com/nodejs/node/commit/954d3f44ef)] - **build**: check Apple clang version in configure script (Michaël Zasso) [#59358](https://github.com/nodejs/node/pull/59358)
* \[[`2b4a09ef8b`](https://github.com/nodejs/node/commit/2b4a09ef8b)] - **build**: fix OpenSSL version detection (Richard Lau) [#59353](https://github.com/nodejs/node/pull/59353)
* \[[`af77e4bf2f`](https://github.com/nodejs/node/commit/af77e4bf2f)] - **build**: update macOS runner and Xcode (Michaël Zasso) [#59238](https://github.com/nodejs/node/pull/59238)
* \[[`86bfdb5528`](https://github.com/nodejs/node/commit/86bfdb5528)] - **build**: remove `nocorepack` `vcbuild` flag (Antoine du Hamel) [#57772](https://github.com/nodejs/node/pull/57772)
* \[[`ebfc28a037`](https://github.com/nodejs/node/commit/ebfc28a037)] - **deps**: update nghttp3 to 1.11.0 (James M Snell) [#59249](https://github.com/nodejs/node/pull/59249)
* \[[`dceb1fca40`](https://github.com/nodejs/node/commit/dceb1fca40)] - **deps**: update ngtcp2 to 1.14.0 (James M Snell) [#59249](https://github.com/nodejs/node/pull/59249)
* \[[`ee36b86ba3`](https://github.com/nodejs/node/commit/ee36b86ba3)] - **deps**: patch V8 to 13.7.152.19 (Node.js GitHub Bot) [#58713](https://github.com/nodejs/node/pull/58713)
* \[[`0b3fc0d7a8`](https://github.com/nodejs/node/commit/0b3fc0d7a8)] - **deps**: patch V8 to 13.7.152.14 (Node.js GitHub Bot) [#58631](https://github.com/nodejs/node/pull/58631)
* \[[`91b3bd3fe6`](https://github.com/nodejs/node/commit/91b3bd3fe6)] - **deps**: patch V8 to 13.7.152.13 (Node.js GitHub Bot) [#58539](https://github.com/nodejs/node/pull/58539)
* \[[`f77a96cd76`](https://github.com/nodejs/node/commit/f77a96cd76)] - **deps**: patch V8 to 13.7.152.10 (Node.js GitHub Bot) [#58446](https://github.com/nodejs/node/pull/58446)
* \[[`910c8796f9`](https://github.com/nodejs/node/commit/910c8796f9)] - **doc**: update BUILDING to reflect Clang 19 changes (Michaël Zasso) [#59782](https://github.com/nodejs/node/pull/59782)
* \[[`34f9b7eab9`](https://github.com/nodejs/node/commit/34f9b7eab9)] - **doc**: reserve NMV 140 for Electron 39 (David Sanders) [#59627](https://github.com/nodejs/node/pull/59627)
* \[[`3f6f6db43f`](https://github.com/nodejs/node/commit/3f6f6db43f)] - **doc**: update minimum Xcode and VS versions (Michaël Zasso) [#59358](https://github.com/nodejs/node/pull/59358)
* \[[`d9fe28bd6b`](https://github.com/nodejs/node/commit/d9fe28bd6b)] - **doc**: fix `CHANGELOG.md` version listing (Antoine du Hamel) [#59299](https://github.com/nodejs/node/pull/59299)
* \[[`0ab50c2768`](https://github.com/nodejs/node/commit/0ab50c2768)] - **doc**: reserve NMV 139 for Electron 38 (Calvin) [#58779](https://github.com/nodejs/node/pull/58779)
* \[[`516b4ebd3c`](https://github.com/nodejs/node/commit/516b4ebd3c)] - **doc**: mark Node.js 23 as End-of-Life (Antoine du Hamel) [#58563](https://github.com/nodejs/node/pull/58563)
* \[[`83052ff9ad`](https://github.com/nodejs/node/commit/83052ff9ad)] - **lib**: add `node:` prefix in sys module deprecation warning (Dario Piotrowicz) [#58442](https://github.com/nodejs/node/pull/58442)
* \[[`d5abfbf582`](https://github.com/nodejs/node/commit/d5abfbf582)] - **lib**: add module to use in module deprecation warnings (Dario Piotrowicz) [#58442](https://github.com/nodejs/node/pull/58442)
* \[[`b4af647920`](https://github.com/nodejs/node/commit/b4af647920)] - **quic**: reduce boilerplate and other minor cleanups (James M Snell) [#59342](https://github.com/nodejs/node/pull/59342)
* \[[`cd9fd09a27`](https://github.com/nodejs/node/commit/cd9fd09a27)] - **quic**: multiple fixups and updates (James M Snell) [#59342](https://github.com/nodejs/node/pull/59342)
* \[[`a6c5d27739`](https://github.com/nodejs/node/commit/a6c5d27739)] - **quic**: update more of the quic to the new compile guard (James M Snell) [#59342](https://github.com/nodejs/node/pull/59342)
* \[[`ee7b8ab29c`](https://github.com/nodejs/node/commit/ee7b8ab29c)] - **quic**: few additional small comment edits in cid.h (James M Snell) [#59342](https://github.com/nodejs/node/pull/59342)
* \[[`c8b64bd023`](https://github.com/nodejs/node/commit/c8b64bd023)] - **quic**: fixup NO\_ERROR macro conflict on windows (James M Snell) [#59381](https://github.com/nodejs/node/pull/59381)
* \[[`e2fefd78e2`](https://github.com/nodejs/node/commit/e2fefd78e2)] - **quic**: fixup windows coverage compile error (James M Snell) [#59381](https://github.com/nodejs/node/pull/59381)
* \[[`99c80e3a45`](https://github.com/nodejs/node/commit/99c80e3a45)] - **quic**: update the guard to check openssl version (James M Snell) [#59249](https://github.com/nodejs/node/pull/59249)
* \[[`0e754fa5d1`](https://github.com/nodejs/node/commit/0e754fa5d1)] - **quic**: start re-enabling quic with openssl 3.5 (James M Snell) [#59249](https://github.com/nodejs/node/pull/59249)
* \[[`eb159a8cfd`](https://github.com/nodejs/node/commit/eb159a8cfd)] - **test**: remove duplicated allocUnsafeSlow test (Michaël Zasso) [#58524](https://github.com/nodejs/node/pull/58524)
* \[[`d93cff5af3`](https://github.com/nodejs/node/commit/d93cff5af3)] - _**Revert**_ "**test**: fix watch tests not including completion messages" (Joyee Cheung) [#58190](https://github.com/nodejs/node/pull/58190)
* \[[`6102159fa1`](https://github.com/nodejs/node/commit/6102159fa1)] - **test**: fix watch tests not including completion messages (Dario Piotrowicz) [#58183](https://github.com/nodejs/node/pull/58183)
* \[[`4bfcad1ac5`](https://github.com/nodejs/node/commit/4bfcad1ac5)] - _**Revert**_ "**watch**: fix watch args not being properly filtered" (Joyee Cheung) [#58190](https://github.com/nodejs/node/pull/58190)
* \[[`4acb854039`](https://github.com/nodejs/node/commit/4acb854039)] - **watch**: fix watch args not being properly filtered (Dario Piotrowicz) [#57936](https://github.com/nodejs/node/pull/57936)
