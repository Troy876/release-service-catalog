# push-rpms-to-pulp

A task to push rpm packages from an OCI artifact to a Pulp repository.

## Parameters

| Name                    | Description                                                                                                                | Optional | Default value              |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------|----------|----------------------------|
| SNAPSHOT_PATH           | Path to the snapshot spec file containing image information                                                                | No       | -                          |
| PULP_DOMAIN             | The domain to use for Pulp operations                                                                                      | No       | -                          |
| PULP_SECRET_NAME        | The name of the secret containing the Pulp cli.toml file. It must have the cli.toml key                                    | No       | -                          |
| DEFAULT_EXCLUDES        | comma-delimited list of file patterns to exclude from the upload                                                           | Yes      | -debuginfo-, -debugsource- |
| resultsDirPath          | Path to the results directory in the data workspace                                                                        | No       | -                          |
| ociStorage              | The OCI repository where the Trusted Artifacts are stored                                                                  | Yes      | empty                      |
| ociArtifactExpiresAfter | Expiration date for the trusted artifacts created in the OCI repository. An empty string means the artifacts do not expire | Yes      | 1d                         |
| trustedArtifactsDebug   | Flag to enable debug logging in trusted artifacts. Set to a non-empty string to enable                                     | Yes      | ""                         |
| orasOptions             | oras options to pass to Trusted Artifacts calls                                                                            | Yes      | ""                         |
| sourceDataArtifact      | Location of trusted artifacts to be used to populate data directory                                                        | Yes      | ""                         |
| dataDir                 | The location where data will be stored                                                                                     | Yes      | /var/workdir/release       |
| taskGitUrl              | The url to the git repo where the release-service-catalog tasks and stepactions to be used are stored                      | No       | -                          |
| taskGitRevision         | The revision in the taskGitUrl repo to be used                                                                             | No       | -                          |
