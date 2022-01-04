# test-renovate-config-validator

```console
$ node -v
v17.1.0

$ ./node_modules/.bin/renovate --version
31.15.0

$ cat renovate.json5 
{
  "packageRules": [
    {
      "matchManagers": ["gomod"],
      "postUpdateOptions": ["gomodTidy"],
    } // This is invalid JSON5. "," is required. renovate-config-validator should fail
    {
      "matchFiles": ["go.mod"],
      "postUpdateOptions": ["gomodTidy"],
    }
  ],
}

$ ./node_modules/.bin/renovate-config-validator 
 INFO: Config validated successfully
```

renovate.json5 is invalid JSON5, but the validation is passed.

CI also passed. https://github.com/suzuki-shunsuke/test-renovate-config-validator/runs/4699431761?check_suite_focus=true

Renovate detected the issue. https://github.com/suzuki-shunsuke/test-renovate-config-validator/issues/1
