# Try out osquery and Fleet

Check out [`fleetctl preview`](https://fleetdm.com/get-started) for a one-step solution to try out Fleet and osquery.  It uses the configuration files in this repository to run Fleet and the necessary dependencies in Docker.

----------------------

### Development

IMPORTANT: 
* The `master` branch is used by `fleetctl` before version 4.5.0 and should not change anymore except for critical fixes.
* The main development and testing branch is `develop`.
* The release branch is `production`.

To make changes to this repository:

#### Development

1. Push a PR on a feature/bugfix branch, target branch should be `develop`.
2. Test `fleetctl preview --preview-config <branch>` with that branch, make sure everything works.
3. Once well tested and the PR is approved, merge PR to the `develop` branch. 

#### QA and Release

If there are no changes on the `develop` branch since last release, simply use: `fleetctl preview`.

If there are changes on the `develop` branch since last release:
1. Test preview with `fleetctl preview --preview-config develop`.
2. Once well tested, create a PR to merge `develop` to the `production` branch at which point every `fleetctl preview` (version 4.5+) user will retrieve it.


