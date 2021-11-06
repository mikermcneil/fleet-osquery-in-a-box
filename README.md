# Try out osquery and Fleet

Check out [`fleetctl preview`](https://fleetdm.com/get-started) for a one-step solution to try out Fleet and osquery.  It uses the configuration files in this repository to run Fleet and the necessary dependencies in Docker.

----------------------

### Development

To make changes to this repository:

* Push a PR on a feature/bugfix branch
* Test `fleetctl preview --preview-config <branch>` with that branch, make sure everything works
* Once well tested, merge to the `production` branch, at which point every `fleetctl preview` (version 4.5+) user will retrieve it
* The `master` branch is used by `fleetctl` before version 4.5.0 and should not change anymore except for critical fixes
