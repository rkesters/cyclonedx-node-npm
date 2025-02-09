# Changelog

All notable changes to this project will be documented in this file.

## unreleased

* Build
  * Disabled TypeScript compilerOption `esModuleInterop` (via [#736])
  * Disabled TypeScript compilerOption `allowSyntheticDefaultImports` (via [#736])

[#736]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/736

## 1.12.0 - 2023-05-17

Based on [OWASP Software Component Verification Standard for Software Bill of Materials](https://scvs.owasp.org/scvs/v2-software-bill-of-materials/)
(SCVS SBOM) criteria, this tool is now capable of producing SBOM documents almost passing Level-2 (only signing needs to be done externally).  
Affective changes based on these SCVS SBOM criteria:
* 2.15 — SPDX license expression detection improved (via [#726])
* 2.18 — SHA-1 integrity hash detection added ([#699] via [#735])

Details
* Changes
  * SPDX license expression detection improved (via [#726])  
    Previously, some expressions were not properly detected, so they were marked as named-license in the SBOM results.
    They should be marked as expression, now.
* Added
  * Added detection for package integrity with SHA-1 ([#699] via [#735])
* Misc
  * Raised dependency `@cyclonedx/cyclonedx-library@^2.0.0`, was `@^1.14.0` (via [#726])

[#699]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/699
[#726]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/726
[#735]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/735

## 1.11.0 - 2023-04-27

* Added
  * SBOM result might be validated (via [#660])  
    This feature is enabled per default and can be disabled via CLI switch `--no-validate`.  
    Validation is skipped, if requirements are not met.
    Requires [transitive optional dependencies](https://github.com/CycloneDX/cyclonedx-javascript-library/blob/main/README.md#optional-dependencies)  

[#660]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/660

## 1.10.0 - 2023-04-17

* Added
  * SBOM result might have `component.scope=optional` populated for OptionalDependencies ([#645] via [#657])  
* Fixed
  * DevDependencies that are also required by OptionalDependencies correctly have the property [`cdx:npm:package:development`](https://github.com/CycloneDX/cyclonedx-property-taxonomy/blob/main/cdx/npm.md) populated in SBOM results ([#645] via [#657])
  * DevDependencies that are also required by OptionalDependencies are correctly omitted from SBOM results, when the CLI switch for omitting "dev" and "optional" are set ([#645] via [#657])
* Docs
  * Describe internal NPM executable detection in README (via [#647])
* Build
  * Use _TypeScript_ `v5.0.4` now, was `v4.9.5` (via [#638])

[#638]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/638
[#645]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/645
[#647]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/647
[#657]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/657

## 1.9.2 - 2023-03-30

* Fixed
  * No longer omit components' version's buildID ([#551] via [#597])  
    Fixed for NPM>=7 only. NPM6 omits this information in the first place, still.
* Misc
  * Utilize SerialNumber generator from [`@cyclonedx/cyclonedx-library@^1.13`](https://github.com/CycloneDX/cyclonedx-javascript-library/releases/tag/v1.13.0) (via [#599])  
    The previously used _internal_ code was donated to that library.

[#551]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/551
[#597]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/597
[#599]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/599

## 1.9.1 - 2023-03-15

* Docs
  * added section "How it works" to the README (via [#563])

[#563]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/563

## 1.9.0 - 2023-03-03

* Changed
  * Detected node packages' metadata are now [normalized](https://www.npmjs.com/package/normalize-package-data), before translation to SBOM components happens. ([#536] via [#537])  
    This might increase the quality of SBOM results.

[#536]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/536
[#537]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/537

## 1.8.0 - 2023-02-16

* Added
  * SBOM result might have additional items in `metadata.tools` populated ([#505] via [#506])

[#505]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/505
[#506]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/506

## 1.7.5 - 2023-02-14

Maintenance release

## 1.7.4 - 2023-02-14

Maintenance release

## 1.7.3 - 2023-02-12

Maintenance release

* Dependencies
  * Utilize _commander_ `^10.0.0` now, was `"^9.4.0` (via [#431])
* Build
  * Use _TypeScript_ `v4.9.5` now, was `v4.9.4` (via [#482])

[#431]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/431
[#482]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/482

## 1.7.2 - 2022-12-19

* Changed
  * Enhanced randomness when generating a `serialNumber` (via [#389])
* Build
  * Use _TypeScript_ `v4.9.4` now, was `v4.9.3` (via [#366])

[#366]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/366
[#389]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/389

## 1.7.1 - 2022-12-16

Maintenance release

* Docs
  * fix CI/CT shield ([badges/shields#8671] via [#378])

[badges/shields#8671]: https://github.com/badges/shields/issues/8671
[#378]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/378

## 1.7.0 - 2022-12-15

* Added
  * SBOM result might have `serialNumber` populated ([#375] via [#376], [#377])

[#375]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/375
[#376]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/376
[#377]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/377

## 1.6.1 - 2022-11-19

Maintenance release

* Docs
  * Enhanced documentation regarding NodeJS/NPM internals, package-dedupe and results (via [#331])
* Misc
  * Added test for flattened results (via [#312])
* Build
  * Use _TypeScript_ `v4.9.3` now, was `v4.8.4` (via [#333])

[#312]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/312
[#331]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/331
[#333]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/333

## 1.6.0 - 2022-11-12

* Added
  * When CLI option `--flatten-components=true` is set, then the property [`cdx:npm:package:bundled`](https://github.com/CycloneDX/cyclonedx-property-taxonomy/blob/main/cdx/npm.md) might be added ([#311] via [#310])
* Misc
  * Added demos for flattened results (via [#310])

[#310]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/310
[#311]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/311

## 1.5.0 - 2022-11-11

* Added
  * Components' install path/location will be visible in the SBOM result ([#305] via [#308])

[#305]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/305
[#308]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/308

## 1.4.1 - 2022-11-06

* Fixed
  * Components' "sha512" hash is properly detected and populated in the SBOM result ([#302] via [#303])

[#302]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/302
[#303]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/303

## 1.4.0 - 2022-11-05

* Added
  * Enabled support for NPM v9 ([#245] via [#246])

[#245]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/245
[#246]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/246

## 1.3.0 - 2022-10-30

* Fixed
  * Improved the NPM compatibility with `--omit` options ([#254] via [#259])
  * In case of an error, the exit code is guaranteed to be non-zero (via [#260])
* Misc
  * Added more debug output regarding NPM version detection (via [#259])

[#254]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/254
[#259]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/259
[#260]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/260

## 1.2.0 - 2022-10-23

* Changed
  * The existence of a lock file is no longer enforced, as long as there are other evidence ([#247] via [#248])

[#247]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/247
[#248]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/248

## 1.1.0 - 2022-10-22

* Added
  * CLI got a new switch `--short-PURLs` ([#225] via [#226])
* Fixed
  * Improved usability on Windows ([#161] via [#234])
* Misc
  * Improved the error message when a lock files was missing ([#196] via [#231])
* Build
  * Use _TypeScript_ `v4.8.4` now, was `v4.8.3` (via [#164])

[#161]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/161
[#164]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/164
[#196]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/196
[#225]: https://github.com/CycloneDX/cyclonedx-node-npm/issues/225
[#226]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/226
[#231]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/231
[#234]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/234

## 1.0.0 - 2022-09-24

First major version (via [#1])

Thanks to all the beta testers. Your efforts, feedback and contributions are appreciated.

[#1]: https://github.com/CycloneDX/cyclonedx-node-npm/pull/1

## 1.0.0-beta.8 - 2022-09-10

* Fixed
  * Run on Windows systems was improved for `npm`/`npx` sub-processes.
* Misc
  * Style: imports are sorted, now.
* Build
  * Use _TypeScript_ `v4.8.3` now, was `v4.8.2`.

## 1.0.0-beta.7 - 2022-09-07

* Changed
  * PackageUrl(PURL) in JSON and XML results are as short as possible, but still precise.

## 1.0.0-beta.6 - 2022-09-06

* Added
  * CLI switch `--ignore-npm-errors` to ignore/suppress NPM errors.

## 1.0.0-beta.5 - 2022-09-06

* Added
  * Support for node 14 was enabled.
  * Support for handling when run via `npx`.
* Docs
  * Improve installation instructions and usage instructions.
* Misc
  * Improved test coverage.
* Build
  * Use _TypeScript_ `v4.8.2` now, was `v4.7.4`.

## 1.0.0-beta.4 - 2022-08-25

* Fixed
  * Run on Windows systems was fixed.
  * Improved error reporting.
  * Debug output was made clearer to understand.

## 1.0.0-beta.3 - 2022-08-23

* Change
  * The package no longer pins dependencies via shrinkwrap.

## 1.0.0-beta.2 - 2022-08-21

* Fixed
  * Debug output was made clearer to understand and less annoying.
* Style
  * Improved internal typing for OmittableDependencyTypes.

## 1.0.0-beta.1 - 2022-08-20

* First feature complete implementation.
