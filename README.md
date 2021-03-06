# webpack stats summary

generates a simple summary of chunk group sizes with optional chunk sizes

### install it

```bash
$ yarn global add webpack-stats-summary
```

### generate a webpack stats file

```bash
$ webpack --config webpack.prod.js --json > stats.json
```

### dump a summary to the console

```bash
$ webpack-stats-summary
```

```
Chunk Group                    Disk KiB Gzip KiB
Total                            753.80   204.67
main                             509.11   149.99
i18n-en-messages-json              2.76     0.81
user-profile                     241.93    53.87
```

Errors and warnings are included by defaultif present in the stats file..

```
 Errors
[at-loader] ./src/something.ts:14:47
    TS6133: 'nogood' is declared but its value is never read.

 Warnings
asset size limit: The following asset(s) exceed the recommended size limit (244 KiB).
This can impact web performance.
Assets:
  js/vendors~main.25a57a75.js (379 KiB)
entrypoint size limit: The following entrypoint(s) combined asset size exceeds the recommended limit (244 KiB). This can impact web performance.
Entrypoints:
  main (438 KiB)
      manifest.js
      js/vendors~main.25a57a75.js
      js/main.4561ef18.js
```

### include chunk details

```bash
$ webpack-stats-summary -c
```

```
Chunk Group              Chunk                                               Disk KiB Gzip KiB
Total                                                                         2058.05   606.22

main                                                                           509.11   149.99
                         manifest.js                                             2.73     1.36
                         js/vendors~main.1a109532.js                           435.15   134.60
                         js/main.08d76402.js                                    71.23    14.02

i18n-en-messages-json                                                            2.76     0.81

user-profile                                                                   241.93    53.87
                         js/vendors~template-editor~user-profile.07ebc8a1.js    93.89    27.69
                         js/template-editor~user-profile.36b873dd.js            97.66    14.49
                         js/user-profile.49a1697b.js                            50.38    11.69
```

### write summary as a markdown file

```bash
$ webpack-stats-summary -o markdown
$ cat webpack-stats-summary.md
```

```
| Chunk Group              | Disk KiB | Gzip KiB |
| ------------------------ | -------- | -------: |
| Total                    |   753.80 |   204.67 |
| main                     |   509.11 |   149.99 |
| i18n-en-messages-json    |     2.76 |     0.81 |
| user-profile             |   241.93 |    53.87 |
```

| Chunk Group           | Disk KiB | Gzip KiB |
| --------------------- | -------- | -------: |
| Total                 | 753.80   |   204.67 |
| main                  | 509.11   |   149.99 |
| i18n-en-messages-json | 2.76     |     0.81 |
| user-profile          | 241.93   |    53.87 |

### write summary as a json file

```bash
$ webpack-stats-summary -o json
```

### set the location of the stats file

```bash
$ webpack-stats-summary -s ./myapp/stats.json
```

### set the location of the build

```bash
$ webpack-stats-summary -b ./myapp/build
```
