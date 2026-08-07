---
name: jadx-cli-apk-decompiler
description: Perform exhaustive JADX source reconstruction, iteratively maximizing recoverable source code and metadata from every DEX file before downstream analysis.
---

Perform a maximum-fidelity JADX decompilation by reconstructing every DEX, class, resource, Kotlin metadata, and deobfuscatable artifact, automatically retrying with alternative JADX options until no additional source code can be recovered.

**Minimal Baseline JADX Command and Options:**

```sh
JAVA_OPTS="-Xmx8g" jadx \
  -d OUTPUT_DIR \
  -j 6 \
  --deobf \
  --deobf-cfg-file-mode overwrite \
  --use-source-name-as-class-name-alias always \
  --source-name-repeat-limit 20 \
  --use-kotlin-methods-for-var-names apply-and-hide \
  -Pkotlin-smap.class-alias-source-dbg=yes \
  -Pkotlin-metadata.class-alias=yes \
  -Pkotlin-metadata.method-args=yes \
  -Pkotlin-metadata.fields=yes \
  -Pkotlin-metadata.companion=yes \
  -Pkotlin-metadata.data-class=yes \
  -Pkotlin-metadata.to-string=yes \
  -Pkotlin-metadata.getters=yes \
  --show-bad-code \
  --comments-level debug \
  <INPUT>.apk
```
