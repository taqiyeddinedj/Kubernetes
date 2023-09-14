# Useful commands for Deployment Startegies (Rolling Update)
``kubectl rollout status deployment alpine-deploy``
``kubectl set image deployment/alpine-deploy alpine-container=alpine:3.7``
``kubectl rollout status deployment alpine-deploy``
### To use previous version of the application:
``kubectl rollout history deployment lightweight-deployment``
### Choose which vrsion to rollout to
``kubectl rollout undo deployment alpine-deploy --to-revision=1 ``
