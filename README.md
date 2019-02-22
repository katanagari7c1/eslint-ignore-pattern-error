# ESLint error processing ignore expressions

To reproduce this issue, run:
```
# cd linter
# npm run test
```

This project emulates an scenario where the node_modules folder is not located in the base dir and a `--ignore-pattern` 
is passed to the CLI. When running eslint, the following error is thrown:

```
TypeError: globPattern.startsWith is not a function
    at relativize (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/util/ignored-paths.js:108:32)
    at IgnoredPaths.addPatternRelativeToCwd (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/util/ignored-paths.js:254:15)
    at new IgnoredPaths (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/util/ignored-paths.js:236:22)
    at lodash.memoize.optionsObj (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/util/glob-utils.js:193:13)
    at memoized (/home/user/Projects/eslint-test/linter/node_modules/lodash/lodash.js:10553:27)
    at resolvedGlobPatterns.map.pattern (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/util/glob-utils.js:224:30)
    at Array.map (<anonymous>)
    at Object.listFilesToProcess (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/util/glob-utils.js:203:61)
    at CLIEngine.executeOnFiles (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/cli-engine.js:586:36)
    at Object.execute (/home/user/Projects/eslint-test/linter/node_modules/eslint/lib/cli.js:197:111)

``` 
