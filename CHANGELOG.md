# Changelog

## [5.4.0](https://github.com/extra2000/elastic-kibana-pod/compare/v5.3.0...v5.4.0) (2022-05-25)


### Features

* **dockerfiles:** upgrade Kibana from `8.2.0` to `8.2.1` ([125678b](https://github.com/extra2000/elastic-kibana-pod/commit/125678bb0f2521ab385481203650b8c7a82c3490))


### Continuous Integrations

* **AppVeyor:** disable test due to Kubic broken mirror ([5177f1d](https://github.com/extra2000/elastic-kibana-pod/commit/5177f1dbf73ed56cc95013dcf285da69d7ed4e01))

## [5.3.0](https://github.com/extra2000/elastic-kibana-pod/compare/v5.2.0...v5.3.0) (2022-05-05)


### Features

* **dockerfiles:** update Kibana from `8.1.2` to `8.2.0` ([5ca1a1c](https://github.com/extra2000/elastic-kibana-pod/commit/5ca1a1c1685eff800b34b3ea51ba6cf530996a76))

## [5.2.0](https://github.com/extra2000/elastic-kibana-pod/compare/v5.1.0...v5.2.0) (2022-04-02)


### Features

* **dockerfile:** update Kibana from `8.1.1` to `8.1.2` ([8ca4cdf](https://github.com/extra2000/elastic-kibana-pod/commit/8ca4cdf2749f2ad1ff1ac8463fcf8fdecd8b1855))

## [5.1.0](https://github.com/extra2000/elastic-kibana-pod/compare/v5.0.0...v5.1.0) (2022-03-31)


### Features

* **dockerfile:** update Kibana from `8.1.0` to `8.1.1` ([f2a9c10](https://github.com/extra2000/elastic-kibana-pod/commit/f2a9c1024d46b3447a36f047dc95d4f2904d7e79))


### Documentations

* **deployment:** simplify `podman generate systemd` ([0a33b22](https://github.com/extra2000/elastic-kibana-pod/commit/0a33b225b8bcbe5a4e85d81e21d21b5e7d8ab79e))

## [5.0.0](https://github.com/extra2000/elastic-kibana-pod/compare/v4.0.0...v5.0.0) (2022-03-31)


### ⚠ BREAKING CHANGES

* **pod:** keystore file is no longer externalized
* **pod:** SSL certs type and mount points have changed
* **deployments:** SSL cert instructions has been removed and replaced with OpenSSL commands from `elastic-elasticsearch-pod` docs

### Features

* **dockerfiles:** upgrade Kibana from verison `8.0.1` to `8.1.0` ([5da0f72](https://github.com/extra2000/elastic-kibana-pod/commit/5da0f72646e4d78146a7cd720e46221da5d7140a))


### Code Refactoring

* **pod:** mount the whole config instead of keystore ([3634e64](https://github.com/extra2000/elastic-kibana-pod/commit/3634e648df9131d8a626dcc1a1499d904eb031af))
* **pod:** simplify certs to PEM via OpenSSL ([ed7c9f5](https://github.com/extra2000/elastic-kibana-pod/commit/ed7c9f548bc549fa9dd75993e6c262b7e89bb645))


### Documentations

* **deployments:** remove SSL cert instructions ([d4ddd3b](https://github.com/extra2000/elastic-kibana-pod/commit/d4ddd3bd7549bf1d352bd477cab4ebf9624f510b))
* **pod:** add `runAsUser` as comment ([d9f810c](https://github.com/extra2000/elastic-kibana-pod/commit/d9f810c47e00fa73055bb9a56eb277501d39e38c))

## [4.0.0](https://github.com/extra2000/elastic-kibana-pod/compare/v3.3.0...v4.0.0) (2022-03-10)


### ⚠ BREAKING CHANGES

* **deployments:** deployment directory has been reorganized

### Features

* **dockerfiles:** update `Kibana` from `8.0.0` to `8.0.1` ([1032076](https://github.com/extra2000/elastic-kibana-pod/commit/1032076d5923b25ce046ced6ad4b4f58ad8bbb86))


### Code Refactoring

* **deployments:** reorganize ([e045483](https://github.com/extra2000/elastic-kibana-pod/commit/e04548389d27aeeaa421fb70c0c7df150a8591fa))
* **docs:** reorganize documentations ([d458f65](https://github.com/extra2000/elastic-kibana-pod/commit/d458f6577d8411aea9fc59c11826d0ad7f2298aa))


### Continuous Integrations

* **AppVeyor:** update workdir path ([dded40b](https://github.com/extra2000/elastic-kibana-pod/commit/dded40b812137319c0a592c725473dddb9a4ed79))

## [3.3.0](https://github.com/extra2000/elastic-kibana-pod/compare/v3.2.0...v3.3.0) (2022-02-20)


### Features

* **dockerfiles:** upgrade Kibana from `7.17.0` to `8.0.0` ([83e32eb](https://github.com/extra2000/elastic-kibana-pod/commit/83e32ebe24042c2a96d7b2445712919ec08be1eb))


### Code Refactoring

* **deployments:** remove `podman-elk-rpi` deployment ([a6e8f12](https://github.com/extra2000/elastic-kibana-pod/commit/a6e8f12bde6bbf308270aee1d79ef1fc9baa6639))
* **deployments:** remove `podman-elk` deployment ([e2f8bea](https://github.com/extra2000/elastic-kibana-pod/commit/e2f8beab2b35426586d9d57caca12b35078d66d7))

## [3.2.0](https://github.com/extra2000/elastic-kibana-pod/compare/v3.1.0...v3.2.0) (2022-02-17)


### Features

* **dockerfile:** upgrade Kibana from `7.16.3` to `7.17.0` ([036ed50](https://github.com/extra2000/elastic-kibana-pod/commit/036ed50992e5fde52d6b34ec3ccbe1182cd0bf1e))


### Code Refactoring

* **dockerfile:** remove `openssl` installations since Kibana `7.17` and above are using Ubuntu image instead of CentOS ([ace03c1](https://github.com/extra2000/elastic-kibana-pod/commit/ace03c1cc99a5364e95cec1f02506254ffa24c84))


### Documentations

* **deployments:** improve explanations for MinIO instructions ([7293ffd](https://github.com/extra2000/elastic-kibana-pod/commit/7293ffd8f4440ac918195555a48dd36dab0d53b3))

## [3.1.0](https://github.com/extra2000/elastic-kibana-pod/compare/v3.0.0...v3.1.0) (2022-01-29)


### Features

* **dockerfile:** upgrade Kibana from `7.16.2` to `7.16.3` ([b352a9f](https://github.com/extra2000/elastic-kibana-pod/commit/b352a9fd2ff777466215ca751021aec89fb1dba5))


### Documentations

* **logo:** remove logo ([7345e6a](https://github.com/extra2000/elastic-kibana-pod/commit/7345e6a05c5476801cbed66bf4312594e36028ce))

## [3.0.0](https://github.com/extra2000/elastic-kibana-pod/compare/v2.0.1...v3.0.0) (2021-12-31)


### ⚠ BREAKING CHANGES

* **monitoring:** Stack Monitoring for Kibana with self-monitoring is no longer works. Use Metricbeat to send Kibana metrics.

### Features

* **dockerfile:** upgrade Kibana from `7.15.2` to `7.16.2` ([91b9752](https://github.com/extra2000/elastic-kibana-pod/commit/91b975292e466f833a9c48bc067f9b5b774d6a2b))


### Fixes

* **monitoring:** remove deprecated `monitoring.enabled` setting ([50fc65b](https://github.com/extra2000/elastic-kibana-pod/commit/50fc65bbd41a062b3d72f17a2b7b1295dcbb493c))

### [2.0.1](https://github.com/extra2000/elastic-kibana-pod/compare/v2.0.0...v2.0.1) (2021-12-16)


### Documentations

* **general-deployment:** add instruction to configure MinIO ([5213e87](https://github.com/extra2000/elastic-kibana-pod/commit/5213e87e478363713297e4d3f8a6cbaf9bb71cf6))

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
