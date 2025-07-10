# request-and-upload-signature

Tekton task to request and upload a simple signature.
- This task is meant to be used in an internal pipeline that can be triggered frequently
  and is expected to complete as quickly as possible.

## Parameters

| Name                       | Description                                                                                                                   | Optional | Default value                                                                     |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------|----------|-----------------------------------------------------------------------------------|
| pipeline_image             | A docker image of operator-pipeline-images for the steps to run in                                                            | Yes      | quay.io/konflux-ci/release-service-utils:7312e2ecbe67e973edd1f0031acb490d6c961a41 |
| manifest_digests           | List of space separated manifest digests for the signed content, usually in the format sha256:xxx                             | No       | -                                                                                 |
| requester                  | Name of the user that requested the signing, for auditing purposes                                                            | No       | -                                                                                 |
| references                 | List of space separated docker references for the signed content, e.g. registry.com/ns/image:v4.9 registry.com/ns/image:v4.10 | No       | -                                                                                 |
| sig_key_id                 | The signing key id that the content is signed with                                                                            | Yes      | 4096R/55A34A82 SHA-256                                                            |
| sig_key_name               | The signing key name that the content is signed with                                                                          | Yes      | containerisvsign                                                                  |
| pyxis_ssl_cert_secret_name | Kubernetes secret name that contains the Pyxis SSL files                                                                      | No       | -                                                                                 |
| pyxis_ssl_cert_file_name   | The key within the Kubernetes secret that contains the Pyxis SSL cert                                                         | No       | -                                                                                 |
| pyxis_ssl_key_file_name    | The key within the Kubernetes secret that contains the Pyxis SSL key                                                          | No       | -                                                                                 |
| pyxis_threads              | Number of threads used to upload signatures to pyxis                                                                          | Yes      | 5                                                                                 |
| umb_client_name            | Client name to connect to umb, usually a service account name                                                                 | Yes      | operatorpipelines                                                                 |
| umb_listen_topic           | umb topic to listen to for responses with signed content                                                                      | Yes      | VirtualTopic.eng.robosignatory.isv.sign                                           |
| umb_publish_topic          | umb topic to publish to for requesting signing                                                                                | Yes      | VirtualTopic.eng.operatorpipelines.isv.sign                                       |
| umb_url                    | umb host to connect to for messaging                                                                                          | Yes      | umb.api.redhat.com                                                                |
| umb_ssl_cert_secret_name   | Kubernetes secret name that contains the umb SSL files                                                                        | No       | -                                                                                 |
| umb_ssl_cert_file_name     | The key within the Kubernetes secret that contains the umb SSL cert                                                           | No       | -                                                                                 |
| umb_ssl_key_file_name      | The key within the Kubernetes secret that contains the umb SSL key                                                            | No       | -                                                                                 |
| pyxis_url                  | Pyxis instance to upload the signature to                                                                                     | Yes      | https://pyxis.engineering.redhat.com                                              |
| signature_data_file        | The file where the signing response should be placed                                                                          | Yes      | signing_response.json                                                             |
