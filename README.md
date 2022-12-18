# compare-renovate-logs-workflow
Compare Renovate logs for GitHub Actions reusable workflow. Using [korosuke613/analyze-renovate-log](https://github.com/korosuke613/analyze-renovate-log).

> **Warning**<br>
> This project is still under development. Expect breaking changes.

The following summary is displayed in workflow summary.

![image](https://user-images.githubusercontent.com/20027695/208295411-a27dac30-c3c8-474f-b999-6e3b4dc2a9d1.png)

<details>
 <summary>Details of compare.</summary>
 
```diff
--- ./dist/renovate-default-branch-json.json	2022-12-18 11:14:37.715241613 +0000
+++ ./dist/renovate-topic-branch-json.json	2022-12-18 11:14:37.783246372 +0000
@@ -13,13 +13,13 @@
             "depCount": 4
           },
           "regex": {
-            "fileCount": 4,
-            "depCount": 4
+            "fileCount": 3,
+            "depCount": 3
           }
         },
         "total": {
-          "fileCount": 6,
-          "depCount": 11
+          "fileCount": 5,
+          "depCount": 10
         }
       }
     }
@@ -204,6 +204,43 @@
               "currentVersion": "1.49.0",
               "isSingleVersion": true,
               "fixedVersion": "1.49.0"
+            },
+            "goreleaser/goreleaser": {
+              "depName": "goreleaser/goreleaser",
+              "currentValue": "0.183.0",
+              "datasource": "github-releases",
+              "extractVersion": "^v(?<version>.*)$",
+              "replaceString": "goreleaser 0.183.0",
+              "depIndex": 0,
+              "updates": [
+                {
+                  "bucket": "non-major",
+                  "newVersion": "0.184.0",
+                  "newValue": "0.184.0",
+                  "releaseTimestamp": "2021-11-01T16:10:42.000Z",
+                  "newMajor": 0,
+                  "newMinor": 184,
+                  "updateType": "minor",
+                  "branchName": "renovate/goreleaser"
+                },
+                {
+                  "bucket": "major",
+                  "newVersion": "1.13.1",
+                  "newValue": "1.13.1",
+                  "releaseTimestamp": "2022-11-29T01:25:26.000Z",
+                  "newMajor": 1,
+                  "newMinor": 13,
+                  "updateType": "major",
+                  "branchName": "renovate/major-goreleaser"
+                }
+              ],
+              "warnings": [],
+              "versioning": "semver",
+              "sourceUrl": "https://github.com/goreleaser/goreleaser",
+              "registryUrl": "https://github.com",
+              "currentVersion": "0.183.0",
+              "isSingleVersion": true,
+              "fixedVersion": "0.183.0"
             }
           }
         }
```

</details>

## Constraints
- The renovate config in json5 format is not supported.

## Usage

```yaml
name: Compare Renovate logs

on:
  pull_request:

jobs:
  compare-renovate-logs:
    uses: korosuke613/compare-renovate-logs-workflow/.github/workflows/compare-renovate-logs.yaml@v1
    with:
      renovate-config-file: renovate.json
```
