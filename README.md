# rules_js reproducibility

## Issue

On Windows, trying to build the target

```bash
bazel build //frontend
```

results in the following errors:

```bash
PS C:\Users\user\Documents\rules_js_repro> bazel build //frontend
INFO: Repo aspect_rules_js++npm+npm__vite__7.3.3_646383693 defined by rule npm_import_rule in @@aspect_rules_js+//npm/private:npm_import.bzl
INFO: repository @@aspect_rules_js++npm+npm__vite__7.3.3_646383693' used the following cache hits instead of downloading the corresponding file.
 * Hash 'ff85c7d78ed48bb3864e38371db7567b96ab9d94126dfb91cddafd11ced3422e48ed1fa2af446573d188bc3e2fd1766eac42ea034df92955c95e947ad718624c' for https://registry.npmjs.org/vite/-/vite-7.3.3.tgz
If the definition of 'repository @@aspect_rules_js++npm+npm__vite__7.3.3_646383693' was updated, verify that the hashes were also updated.
ERROR: C:/users/user/_bazel_user/yvbvf4ba/external/aspect_rules_js+/npm/private/npm_import.bzl:576:17: An error occurred during the fetch of repository 'aspect_rules_js++npm+npm__vite__7.3.3_646383693':
   Traceback (most recent call last):
        File "C:/users/user/_bazel_user/yvbvf4ba/external/aspect_rules_js+/npm/private/npm_import.bzl", line 599, column 38, in _npm_import_rule_impl
                _download_and_extract_archive(rctx, package_json_only = False)
        File "C:/users/user/_bazel_user/yvbvf4ba/external/aspect_rules_js+/npm/private/npm_import.bzl", line 576, column 17, in _download_and_extract_archive
                fail(msg)
Error in fail: Failed to extract package tarball. '[Label("@@tar.bzl++toolchains+bsd_tar_toolchains_windows_amd64//:tar.exe"), "-xf", "package.tgz", "--strip-components", "1", "-C", "package", "--no-same-owner", "--no-same-permissions", "--exclude", "Makefile", "--exclude", "Gulpfile.js", "--exclude", "Gruntfile.js", "--exclude", "appveyor.yml", "--exclude", "circle.yml", "--exclude", "codeship-services.yml", "--exclude", "codeship-steps.yml", "--exclude", "wercker.yml", "--exclude", ".tern-project", "--exclude", ".gitattributes", "--exclude", ".editorconfig", "--exclude", ".*ignore", "--exclude", ".eslintrc", "--exclude", ".jshintrc", "--exclude", ".flowconfig", "--exclude", ".documentup.json", "--exclude", ".yarn-metadata.json", "--exclude", ".travis.yml", "--exclude", "*.md"]' exited with 256: 
STDOUT:

STDERR:
java.io.IOException: ERROR: src/main/native/windows/process.cc(189): CreateProcessW("C:\users\user\_bazel_user\yvbvf4ba\external\tar.bzl++toolchains+bsd_tar_toolchains_windows_amd64\tar.exe" -xf package.tgz --strip-components 1 -C package --no-same-owner --no-same-permissions --exclude Makefile --exclude Gulpfile.js --exclude Gruntfile.js --exclude appveyor.yml --exclude circle.yml --exclude codeship-services.yml --exclude codeship-steps.yml --exclude wercker.yml --exclude .tern-project --exclude .gitattributes --exclude .editorconfig --exclude .*ignore --exclude .(...)): Access is denied.
 (error: 5)
WARNING: Target pattern parsing failed.
ERROR: Skipping '//frontend': no such package '@@aspect_rules_js++npm+npm__vite__7.3.3_646383693//': Failed to extract package tarball. '[Label("@@tar.bzl++toolchains+bsd_tar_toolchains_windows_amd64//:tar.exe"), "-xf", "package.tgz", "--strip-components", "1", "-C", "package", "--no-same-owner", "--no-same-permissions", "--exclude", "Makefile", "--exclude", "Gulpfile.js", "--exclude", "Gruntfile.js", "--exclude", "appveyor.yml", "--exclude", "circle.yml", "--exclude", "codeship-services.yml", "--exclude", "codeship-steps.yml", "--exclude", "wercker.yml", "--exclude", ".tern-project", "--exclude", ".gitattributes", "--exclude", ".editorconfig", "--exclude", ".*ignore", "--exclude", ".eslintrc", "--exclude", ".jshintrc", "--exclude", ".flowconfig", "--exclude", ".documentup.json", "--exclude", ".yarn-metadata.json", "--exclude", ".travis.yml", "--exclude", "*.md"]' exited with 256: 
STDOUT:

STDERR:
java.io.IOException: ERROR: src/main/native/windows/process.cc(189): CreateProcessW("C:\users\user\_bazel_user\yvbvf4ba\external\tar.bzl++toolchains+bsd_tar_toolchains_windows_amd64\tar.exe" -xf package.tgz --strip-components 1 -C package --no-same-owner --no-same-permissions --exclude Makefile --exclude Gulpfile.js --exclude Gruntfile.js --exclude appveyor.yml --exclude circle.yml --exclude codeship-services.yml --exclude codeship-steps.yml --exclude wercker.yml --exclude .tern-project --exclude .gitattributes --exclude .editorconfig --exclude .*ignore --exclude .(...)): Access is denied.
 (error: 5)
ERROR: no such package '@@aspect_rules_js++npm+npm__vite__7.3.3_646383693//': Failed to extract package tarball. '[Label("@@tar.bzl++toolchains+bsd_tar_toolchains_windows_amd64//:tar.exe"), "-xf", "package.tgz", "--strip-components", "1", "-C", "package", "--no-same-owner", "--no-same-permissions", "--exclude", "Makefile", "--exclude", "Gulpfile.js", "--exclude", "Gruntfile.js", "--exclude", "appveyor.yml", "--exclude", "circle.yml", "--exclude", "codeship-services.yml", "--exclude", "codeship-steps.yml", "--exclude", "wercker.yml", "--exclude", ".tern-project", "--exclude", ".gitattributes", "--exclude", ".editorconfig", "--exclude", ".*ignore", "--exclude", ".eslintrc", "--exclude", ".jshintrc", "--exclude", ".flowconfig", "--exclude", ".documentup.json", "--exclude", ".yarn-metadata.json", "--exclude", ".travis.yml", "--exclude", "*.md"]' exited with 256: 
STDOUT:

STDERR:
java.io.IOException: ERROR: src/main/native/windows/process.cc(189): CreateProcessW("C:\users\user\_bazel_user\yvbvf4ba\external\tar.bzl++toolchains+bsd_tar_toolchains_windows_amd64\tar.exe" -xf package.tgz --strip-components 1 -C package --no-same-owner --no-same-permissions --exclude Makefile --exclude Gulpfile.js --exclude Gruntfile.js --exclude appveyor.yml --exclude circle.yml --exclude codeship-services.yml --exclude codeship-steps.yml --exclude wercker.yml --exclude .tern-project --exclude .gitattributes --exclude .editorconfig --exclude .*ignore --exclude .(...)): Access is denied.
 (error: 5)
INFO: Elapsed time: 2.053s
INFO: 0 processes.
ERROR: Build did NOT complete successfully
```

## Expectations

The target should build correctly on Windows.
It does work on Linux, so either I'm inadvertently exploiting some undocumented features on Linux, or the Windows build is broken.

## Additional info

The errors seem somewhat related to [#2026](https://github.com/aspect-build/rules_js/issues/2026), but adding the `custom_postinstalls` (ignoring the fact that they would just raise an error on Windows) does not seem to fix the issue.

## Version info

Tested with

- Bazel version 9.1.0
- Bazel version 8.7.0
