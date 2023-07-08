@@ -82,7 +82,7 @@ target_migrate(){
        echo "-- build sw-migrate --" >&2
        TMP_DOCKERFILE="/tmp/${RANDOM}.dockerfile"
        envsubst < $SW_ROOT/paas/migrate/Dockerfile.tpl > ${TMP_DOCKERFILE}
        docker build -t sw-migrate:$tag --pull --no-cache -f ${TMP_DOCKERFILE} $SW_ROOT/paas/migrate
        docker build -t sw-migrate:$tag -f ${TMP_DOCKERFILE} $SW_ROOT/paas/migrate
        docker tag sw-migrate:$tag sw-migrate:latest
    fi
    if [ -n "$PUSH_REPO" ]; then
@@ -98,7 +98,7 @@ target_progress_check(){
        echo "-- build sw-progress-check --" >&2
        TMP_DOCKERFILE="/tmp/${RANDOM}.dockerfile"
        envsubst < $SW_ROOT/paas/progress-check/Dockerfile.tpl > ${TMP_DOCKERFILE}
        docker build -t sw-progress-check:$tag --pull --no-cache -f ${TMP_DOCKERFILE} $SW_ROOT/paas/progress-check
        docker build -t sw-progress-check:$tag -f ${TMP_DOCKERFILE} $SW_ROOT/paas/progress-check
        docker tag sw-progress-check:$tag sw-progress-check:latest
    fi
    if [ -n "$PUSH_REPO" ]; then
@@ -112,7 +112,7 @@ target_openjdk8(){
    [ -n "$TAG" ] && tag=$TAG || tag="latest"
    if [ -n "$BUILD" ]; then
        echo "-- build sw-openjdk8-jre --" >&2
        docker build -t sw-openjdk8-jre:$tag --pull --no-cache -f $SW_ROOT/paas/openjdk8-jre/Dockerfile $SW_ROOT/paas/openjdk8-jre
        docker build -t sw-openjdk8-jre:$tag -f $SW_ROOT/paas/openjdk8-jre/Dockerfile $SW_ROOT/paas/openjdk8-jre
        docker tag sw-openjdk8-jre:$tag sw-openjdk8-jre:latest
    fi
    if [ -n "$PUSH_REPO" ]; then
@@ -128,7 +128,7 @@ target_postrun(){
        echo "-- build sw-postrun --" >&2
        TMP_DOCKERFILE="/tmp/${RANDOM}.dockerfile"
        envsubst < $SW_ROOT/paas/postrun/Dockerfile.tpl > ${TMP_DOCKERFILE}
        docker build -t sw-postrun:$tag --pull --no-cache -f ${TMP_DOCKERFILE} $SW_ROOT/paas/postrun
        docker build -t sw-postrun:$tag -f ${TMP_DOCKERFILE} $SW_ROOT/paas/postrun
        docker tag sw-postrun:$tag sw-postrun:latest
    fi
    if [ -n "$PUSH_REPO" ]; then
  2 changes: 1 addition & 1 deletion2  
chart/sreworks-chart/charts/appmanager/templates/rbac.yaml
@@ -331,4 +331,4 @@ subjects:
- kind: ServiceAccount
  name: default
  namespace: {{ .Release.Namespace }}
{{ end }}
{{ end }}# 6688668
