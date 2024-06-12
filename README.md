# Repro for issue 7311

## Versions

firebase-tools: 13.11.2<br>

## Steps to reproduce

1. (Optional) Run `firebase remoteconfig:get --output remoteconfig.template.json --project PROEJCT_ID_1`
   - This gets the Firebase project's Remote Config template.
   - The output of running this command is in the `remoteconfig.template.json`
1. Run `firebase deploy --only remoteconfig --project cli-testproject-01`
   - Error is raised

```
[error] Error: HTTP Error: 400, [VALIDATION_ERROR]: INVALID_ROLLOUT_PARAM_VALUE The template has an invalid rollout id : rollout_1
[debug] [2024-06-12T15:25:39.802Z] Error Context: {
  "body": {
    "error": {
      "code": 400,
      "message": "[VALIDATION_ERROR]: INVALID_ROLLOUT_PARAM_VALUE The template has an invalid rollout id : rollout_1",
      "status": "INVALID_ARGUMENT",
      "details": [
        {
          "@type": "type.googleapis.com/google.rpc.DebugInfo",
          "detail": "[ORIGINAL ERROR] generic::invalid_argument: com.google.net.rpc3.client.RpcClientException: <eye3 title='/DevelopersRemoteConfigManagementExternalService.UpdateRemoteConfig, INVALID_ARGUMENT'/> APPLICATION_ERROR;google.firebase.remoteconfig.v1/DevelopersRemoteConfigManagementExternalService.UpdateRemoteConfig;com.google.developers.mobile.remoteconfig.common.RemoteConfigException: [VALIDATION_ERROR]: INVALID_ROLLOUT_PARAM_VALUE The template has an invalid rollout id : rollout_1;AppErrorCode=3;StartTimeMs=1718205938504;unknown;Deadline(sec)=10.0;ResFormat=uncompressed;ServerTimeSec=1.039015403;LogBytes=256;FailFast;EffSecLevel=none;ReqFormat=uncompressed;ReqID=a70dd45fd89b6b70;GlobalID=0;Server=[2002:a05:6d08:3ce8::]:4139 [google.rpc.error_details_ext] { message: \"[VALIDATION_ERROR]: INVALID_ROLLOUT_PARAM_VALUE The template has an invalid rollout id : rollout_1\" details { type_url: \"type.googleapis.com/google.internal.firebase.remoteconfig.v1.RemoteConfigErrorPayload\" value: \"\\010\\006\\022NINVALID_ROLLOUT_PARAM_VALUE The template has an invalid rollout id : rollout_1\\032\\014\\n\\010template\\020\\002\" } }"
        }
      ]
    }
  },
  "response": {
    "statusCode": 400
  }
}
```
