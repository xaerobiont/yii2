Yii Versioning
==============

This document summarizes the versioning policy of Yii. Our current versioning strategy can be
described as [ferver](https://github.com/jonathanong/ferver), which we considered is more practical
and reasonable than [Semantic Versioning](http://semver.org/) (See [#7408](https://github.com/yiisoft/yii2/issues/7408) for more references).

Within the core developer team, we have emphasized several times that it is important to keep 2.0.x releases 100% BC-compatible.
But this is an ideal plan. The ferver article has given out a real world example that this is hard to achieve in practice,
regardless you are using semver or not.

In summary, our versioning policy for Yii 2 is as follows:

## Version numbers

Version numbers are in the format of `2.x.y.z`.

A possible Yii version 3 is not covered here as we'd expect it to be like 2.0 over 1.0. We expect this only happens every 3 to 5 years,
depending on external technology advancement (such as PHP upgraded from 5.0 to 5.4).

### `2.X.0`: major releases

BC-breaking releases, which contain major features and changes that may break BC. Upgrading from earlier versions may
not be trivial, but a complete upgrade guide or even script will be available.

* Mainly contain new features and bug fixes
* Contain minor features and bug fixes merged from patch releases.
* May contain BC-breaking changes which are recorded in `UPGRADE-2.X.md` file.
* Release cycle is around 12 months or more.
* Require pre-releases: `2.X.0-alpha`, `2.X.0-beta`, `2.X.0-rc`.
* Requires major news releases and marketing effort.


### `2.x.Y`: minor releases

Patch releases, which should be 100% BC-compatible. Ideally, we hope they contain only changes that do not affect backwards compatibilty
however it is not always possible to keep 100% BC-compatible, so upgrade notes are recorded in `UPGRADE.md`.
Practically, since 2.0.x is released more frequently, we are also adding minor features
to it so that users can enjoy them earlier.

* Mainly contain bug fixes and minor feature enhancements
* No major features.
* Should be 100% backward compatible to ensure worry-free upgrade. Only a few exceptions are allow which are documented in `UPGRADE.md`.
* Release cycle is around 1 to 2 months.
* No pre-releases (alpha, beta, RC) needed.
* Should be merged back to master branch constantly (at least once every week manually).
* With news announcements. Project site will be updated.


### `2.x.y.Z`: patch releases

Patch releases, which should be 100% BC-compatible, containing bug fixes only.
Release cycle is around 1 to 2 weeks. No news announcement or project site update (unless it contains major/security issue fixes).
The release process will be made mostly automatic.

* containing bug fixes only, no features included.
* Must be 100% backward compatible to ensure worry-free upgrade. Only exception is security issues that may require breaking BC.
* Release cycle is around 1 to 2 months.
* No pre-releases (alpha, beta, RC) needed.
* Should be merged back to master branch constantly (at least once every week manually).


## Branching policy

WIP - this is not complete yet.

* `master` branch is the dev branch for the current major release.
  Once a new minor release `2.n` is ready, create a maintenance branch named `2.n.x` off `master`.
  E.g. a `2.0.x` branch is created if version `2.1` will be developed on `master`
  (cmp. [composer branch naming schema](https://getcomposer.org/doc/02-libraries.md#branches)).
* Create tags `2.x.y.z` and `2.x.y` branch to mark patch releases (including `2.x.y.0` release).
* Changes on `2.n.x` branches will be merged back to `master` constantly.
* For the next major release, create a dev branch named `2.t.x`. Once the next major release is ready, it will be merged to `master`, and then create a `2.t.0` branch off `master` (the old `2.t-dev` branch will be deleted to avoid confusion).



## Releases

Both Yii2  Framework and official extension projects follow the above versioning and branching policies.
Framework and official extension projects are released independently of each other, i.e. version number mismatch between framework and extension is expected.
The Application Templates are always released together with the framework.

The release cycles described above only apply to the core framework.
Extensions and application templates are released on demand.
It is likely that an extension has no new releases for a very long time because it does not receive any bug fixes or enhancements.
