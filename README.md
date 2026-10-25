# PHP for Web IDE

The PHP language pack of [Web IDE](https://github.com/antennae-space/web-ide): the highlighting of PHP, a language server (diagnostics, completion, navigation, rename, formatting, the structure of a file) and the test pattern `{name}Test.php`. An official plugin: the IDE installs it by default.

## What it needs

- **Install from the IDE**: a PHP file without a server shows a banner, *Install intelephense* (also in *Settings → Plugins*): the IDE runs npm in a console, into its own folder (`~/.local/share/web-ide/tools/lang-php`). You need node and npm.
- **intelephense** (`npm install -g intelephense`), or else **phpactor** (its phar, or `composer global require phpactor/phpactor`), on your PATH.
- The IDE runs it **confined**: it reads your project (not write), the program and its package (intelephense: the node on your PATH, `NODE`, and its package, `INTELEPHENSE`; phpactor: its composer `vendor` folder or the folder of its phar, `PHPACTOR`), keeps its caches in its own folder, and has no network.
- On a project over SSH, the server runs on its host, as you installed it there.

## Permissions

| | |
|---|---|
| `program:intelephense`, `program:phpactor` | run the server, confined |
| `path:NODE` | read the node that runs intelephense |
| `path:INTELEPHENSE`, `path:PHPACTOR` | read the server's package |

## Develop

A pack is data: `plugin.json` (checked by `node scripts/check.mjs` against the [plugin SDK](https://github.com/antennae-space/plugin-sdk)'s schema) and `grammars/php.json` (a grammar of the IDE's editor). `./scripts/pack.sh` builds the archives; a tag `v*` publishes a release.

## License

MIT.
