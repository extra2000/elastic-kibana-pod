# Changelog

## [2.0.0](https://github.com/extra2000/elastic-kibana-pod/compare/v1.2.0...v2.0.0) (2021-11-29)


### ⚠ BREAKING CHANGES

* **pods:** existing pods have been removed and changed into example files
* **deployments:** we no longer support rootful deployments

### Documentations

* **deployments:** add instructions to `chcon` configs ([fd1168c](https://github.com/extra2000/elastic-kibana-pod/commit/fd1168c41f02d1fdbe407277fa547d17e65fac32))
* **deployments:** add instructions to check certificate ([d2817d5](https://github.com/extra2000/elastic-kibana-pod/commit/d2817d5f517de3595cef5e47c3c050b2418baf34))
* **deployments:** add instructions to clone repository ([aeff64a](https://github.com/extra2000/elastic-kibana-pod/commit/aeff64adb80ece9e4c188bdd1453c8b00153b9aa))
* **deployments:** add instructions to distribute secrets to nodes ([eebbb7d](https://github.com/extra2000/elastic-kibana-pod/commit/eebbb7d7b2c398610b63479aeb875ca2696da467))
* **deployments:** change from rootful to rootless Podman ([d16914f](https://github.com/extra2000/elastic-kibana-pod/commit/d16914f9d87fa1f72eafb01f653e046bc0d53f9a))
* **deployments:** don't distribute `elastic-ca.p12` ([d2b29ef](https://github.com/extra2000/elastic-kibana-pod/commit/d2b29ef4e4816e56478947ecb98a53f47d5e4b19))
* **deployments:** improve `cd` instructions ([6a1f901](https://github.com/extra2000/elastic-kibana-pod/commit/6a1f9013b891bc6605f2b7dea0bbc32f67943f97))
* **host-preparations:** update instructions for rootless Podman ([b205549](https://github.com/extra2000/elastic-kibana-pod/commit/b205549f2ea1f0fcfd763df8fbb6f1d17cc14686))
* **sections:** change Section name for deployments ([30a26bc](https://github.com/extra2000/elastic-kibana-pod/commit/30a26bc8287cf2ed70f62c4c0109d95389607910))


### Code Refactoring

* **pods:** remove `runAsGroup` and `runAsUser` ([67365fa](https://github.com/extra2000/elastic-kibana-pod/commit/67365fa7602761de26326bc209ff99dd3c464dd2))
* **pods:** remove existing pods and changed into example ([449afc2](https://github.com/extra2000/elastic-kibana-pod/commit/449afc26300053153f6b42cf6acb0b0c872114fa))
* **selinux:** remove unnecessary `user_home_t` ([7eb4d08](https://github.com/extra2000/elastic-kibana-pod/commit/7eb4d0865bf4030bb856e337085cdcdfe2faea57))
* **sphinx:** change layout to full width ([4d1908c](https://github.com/extra2000/elastic-kibana-pod/commit/4d1908cc10644c30a33b70f0ca0f818127c5257d))

## [1.2.0](https://github.com/extra2000/elastic-kibana-pod/compare/v1.1.1...v1.2.0) (2021-11-12)


### Features

* **kibana:** update version from `7.15.1` to `7.15.2` ([c420851](https://github.com/extra2000/elastic-kibana-pod/commit/c4208510263b7d45e4f59be4474e9bfdbb590c35))

### [1.1.1](https://github.com/extra2000/elastic-kibana-pod/compare/v1.1.0...v1.1.1) (2021-11-02)


### Documentations

* **configs:** add more default configurations ([ba04d12](https://github.com/extra2000/elastic-kibana-pod/commit/ba04d12aed1694249d53186ad7e4a9612943a016))
* **configs:** rename `xpack.monitoring.` to `monitoring.` ([ec53b9a](https://github.com/extra2000/elastic-kibana-pod/commit/ec53b9a86ba7b6d73cb026cd92a23d8f6b46b705))


### Fixes

* **dockerfile:** add missing `openssl` package ([edbeeb7](https://github.com/extra2000/elastic-kibana-pod/commit/edbeeb7d25a6970ad238aa61d6859d12b8bb0453))

## [1.1.0](https://github.com/extra2000/elastic-kibana-pod/compare/v1.0.0...v1.1.0) (2021-10-25)


### Features

* **kibana:** upgrade from version `7.15.0` to `7.15.1` ([bc49cee](https://github.com/extra2000/elastic-kibana-pod/commit/bc49cee8f261f62f726fdde26ef282066b702ba4))


### Documentations

* **configs:** add missing `server.publicBaseUrl` ([a9f0f83](https://github.com/extra2000/elastic-kibana-pod/commit/a9f0f83726dca44ee17604a0dc2a7eb654651ba6))

## 1.0.0 (2021-10-23)


### Features

* initial release ([54f3260](https://github.com/extra2000/elastic-kibana-pod/commit/54f3260e0dc43a5e559c5b9cb8d2df5a8759ab3c))


### Documentations

* **README:** update `README.md` ([bb294fa](https://github.com/extra2000/elastic-kibana-pod/commit/bb294fa0f28364a2126f2e848e90d2f3fe4d468a))


### Continuous Integrations

* add AppVeyor with `semantic-release` ([d52e024](https://github.com/extra2000/elastic-kibana-pod/commit/d52e024f64be42329144a88690d62b74c7b0c299))
