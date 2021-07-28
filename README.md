# search

![Version: 0.1.1-dev](https://img.shields.io/badge/Version-0.1.1--dev-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

A Helm chart for Helx Search components. This chart installs Dug, TranQL , Airflow and Redis.

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://airflow-helm.github.io/charts | airflow | 8.1.3 |
| https://charts.bitnami.com/bitnami | redis | 13.0.0 |
| https://helm.elastic.co | elasticsearch | 7.12.0 |
| https://helx-charts.github.io/charts/ | tranql | 0.1.3 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| airflow.airflow.config.AIRFLOW__CORE__LOAD_EXAMPLES | string | `"FALSE"` |  |
| airflow.airflow.config.AIRFLOW__KUBERNETES__DELETE_WORKER_PODS | string | `"TRUE"` |  |
| airflow.airflow.config.AIRFLOW__SCHEDULER__SCHEDULE_AFTER_TASK_EXECUTION | string | `"FALSE"` |  |
| airflow.airflow.config.AIRFLOW__WEBSERVER__BASE_URL | string | `""` |  |
| airflow.airflow.configSecretsName | string | `"airflow-config-secrets"` |  |
| airflow.airflow.executor | string | `"KubernetesExecutor"` |  |
| airflow.airflow.extraVolumeMounts[0].mountPath | string | `"/opt/airflow/share/data"` |  |
| airflow.airflow.extraVolumeMounts[0].name | string | `"airflow-data"` |  |
| airflow.airflow.extraVolumes[0].name | string | `"airflow-data"` |  |
| airflow.airflow.extraVolumes[0].persistentVolumeClaim.claimName | string | `"search-data"` |  |
| airflow.airflow.image.pullPolicy | string | `"Always"` |  |
| airflow.airflow.image.repository | string | `"helxplatform/roger"` |  |
| airflow.airflow.image.tag | string | `"0.3.0"` |  |
| airflow.airflow.kubernetesPodTemplate.resources | object | `{}` |  |
| airflow.dags.gitSync.branch | string | `"main"` |  |
| airflow.dags.gitSync.enabled | bool | `true` |  |
| airflow.dags.gitSync.repo | string | `"https://github.com/helxplatform/roger.git"` |  |
| airflow.dags.gitSync.repoSubPath | string | `"dags"` |  |
| airflow.dags.gitSync.revision | string | `"HEAD"` |  |
| airflow.dags.gitSync.syncWait | int | `60` |  |
| airflow.enabled | bool | `true` |  |
| airflow.externalRedis.host | string | `"search-redis-master"` |  |
| airflow.externalRedis.passwordSecret | string | `"search-redis-secret"` |  |
| airflow.externalRedis.passwordSecretKey | string | `"password"` |  |
| airflow.flower.enabled | bool | `false` |  |
| airflow.logs.path | string | `"/opt/airflow/share/logs"` |  |
| airflow.logs.persistence.accessMode | string | `"ReadWriteMany"` |  |
| airflow.logs.persistence.enabled | bool | `true` |  |
| airflow.logs.persistence.size | string | `"1Gi"` |  |
| airflow.logs.persistence.storageClass | string | `""` |  |
| airflow.redis.enabled | bool | `false` |  |
| airflow.workers.enabled | bool | `false` |  |
| api.appName | string | `"webserver"` |  |
| api.debug | bool | `false` |  |
| api.deployment.apiPort | int | `5551` |  |
| api.deployment.apiTimeout | int | `10` |  |
| api.deployment.apiWorkers | int | `4` |  |
| api.deployment.extraEnv | list | `[]` |  |
| api.deployment.imagePullSecrets | list | `[]` |  |
| api.deployment.logLevel | string | `"INFO"` |  |
| api.deployment.resources | object | `{}` |  |
| api.image.pullPolicy | string | `"IfNotPresent"` |  |
| api.image.repository | string | `"helxplatform/dug"` |  |
| api.image.tag | string | `"2.3.0"` |  |
| api.service.annotations | object | `{}` |  |
| api.service.apiPort | string | `"5551"` |  |
| api.service.name | string | `"search-api"` |  |
| api.service.type | string | `"ClusterIP"` |  |
| elasticsearch.clusterName | string | `"search-elasticsearch"` |  |
| elasticsearch.enabled | bool | `true` |  |
| elasticsearch.extraEnvs[0].name | string | `"ELASTIC_PASSWORD"` |  |
| elasticsearch.extraEnvs[0].valueFrom.secretKeyRef.key | string | `"password"` |  |
| elasticsearch.extraEnvs[0].valueFrom.secretKeyRef.name | string | `"search-elastic-secret"` |  |
| elasticsearch.extraEnvs[1].name | string | `"ELASTIC_USERNAME"` |  |
| elasticsearch.extraEnvs[1].valueFrom.secretKeyRef.key | string | `"username"` |  |
| elasticsearch.extraEnvs[1].valueFrom.secretKeyRef.name | string | `"search-elastic-secret"` |  |
| elasticsearch.imageTag | string | `"7.12.0"` |  |
| elasticsearch.replicas | int | `1` |  |
| nboost.enabled | bool | `false` |  |
| persistence.pvcSize | string | `"1Gi"` |  |
| persistence.storageClass | string | `""` |  |
| redis.cluster.slaveCount | int | `1` |  |
| redis.clusterDomain | string | `"cluster.local"` |  |
| redis.enabled | bool | `true` |  |
| redis.existingSecret | string | `"search-redis-secret"` |  |
| redis.existingSecretPasswordKey | string | `"password"` |  |
| redis.image.repository | string | `"redislabs/redisgraph"` |  |
| redis.image.tag | string | `"2.2.14"` |  |
| redis.master.command | string | `""` |  |
| redis.master.extraFlags[0] | string | `"--loadmodule /usr/lib/redis/modules/redisgraph.so"` |  |
| redis.master.livenessProbe.enabled | bool | `false` |  |
| redis.master.readinessProbe.enabled | bool | `false` |  |
| redis.master.resources.requests.cpu | string | `"200m"` |  |
| redis.master.resources.requests.memory | string | `"8Gi"` |  |
| redis.master.service.port | int | `6379` |  |
| redis.persistence.existingClaim | string | `"redis-data"` |  |
| redis.redis.command | string | `"redis-server"` |  |
| redis.slave.command | string | `""` |  |
| redis.slave.extraFlags[0] | string | `"--loadmodule /usr/lib/redis/modules/redisgraph.so"` |  |
| redis.slave.livenessProbe.enabled | bool | `false` |  |
| redis.slave.readinessProbe.enabled | bool | `false` |  |
| redis.slave.resources.requests.cpu | string | `"200m"` |  |
| redis.slave.resources.requests.memory | string | `"8Gi"` |  |
| redis.slave.service.port | int | `6379` |  |
| redis.usePassword | bool | `true` |  |
| secrets.elastic.name | string | `"search-elastic-secret"` |  |
| secrets.elastic.passwordKey | string | `"password"` |  |
| secrets.elastic.user | string | `"elastic"` |  |
| secrets.elastic.userKey | string | `"username"` |  |
| secrets.redis.name | string | `"search-redis-secret"` |  |
| secrets.redis.passwordKey | string | `"password"` |  |
| tranql.enabled | bool | `true` |  |
| tranql.existingRedis.host | string | `"search-redis-slave"` |  |
| tranql.existingRedis.port | int | `6379` |  |
| tranql.existingRedis.secret | string | `"search-redis-secret"` |  |
| tranql.existingRedis.secretPasswordKey | string | `"password"` |  |
| tranql.extraEnv[0].name | string | `"WEB_PATH_PREFIX"` |  |
| tranql.extraEnv[0].value | string | `"/tranql"` |  |
| tranql.redis.enabled | bool | `false` |  |
| ui.api_url | string | `"http://localhost:5551"` |  |
| ui.appPort | int | `8080` |  |
| ui.app_name | string | `"ui"` |  |
| ui.containerPort | int | `8080` |  |
| ui.container_port | int | `8080` |  |
| ui.enabled | bool | `true` |  |
| ui.extraEnv[0].name | string | `"PUBLIC_URL"` |  |
| ui.extraEnv[0].value | string | `"/ui"` |  |
| ui.http_port | int | `8080` |  |
| ui.image.pullPolicy | string | `"Always"` |  |
| ui.image.repository | string | `"cschreep/helx-search-ui"` |  |
| ui.image.tag | string | `"1.1.1-dev"` |  |
| ui.imagePullSecrets | list | `[]` |  |
| ui.node_env | string | `"development"` |  |
| ui.resources.limits.cpu | string | `"200m"` |  |
| ui.resources.limits.memory | string | `"320Mi"` |  |
| ui.resources.requests.cpu | string | `"50m"` |  |
| ui.resources.requests.memory | string | `"64Mi"` |  |
| ui.service.annotations | object | `{}` |  |
| ui.service.name | string | `"ui"` |  |
| ui.service.servicePort | int | `8080` |  |
| ui.service.type | string | `"ClusterIP"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
