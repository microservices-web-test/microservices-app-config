# microservices-app-config
GitOps repo watched by Argo CD. One folder per service under `apps/`.
- `apps/<service>/`  – kustomize app (manifests, migrations, SealedSecrets). Image tag lives in `kustomization.yaml` (`images[].newTag`), updated by Jenkins CI.
- `argocd/`          – Argo CD `Application` manifests (apply once with `kubectl apply -f`).
Secrets: never commit plain Secrets. Seal them with `kubeseal` (see apps/auth-service/sealed-secrets.yaml).
