# GKE fleet rotation manifests (GitOps)

Fleet node pool version targets for Aiden Infrastructure Lifecycle demos.

- **Repo:** `craigleander/application-manifiests`
- **Layout:** `gke-fleet/<stack-id>/<pool>-nodepool.yaml`
- **Pipeline:** Aiden commits to `aiden/fleet-k8s-*` branches — demo stops before merge to `main`

## Target version (demo)

**Kubernetes 1.29.0** — latest fleet-wide rotation target.

Each manifest sets:

```yaml
spec:
  kubernetesVersion: "1.29.0"
  upgradeSettings:
    maxSurge: 2
    maxUnavailable: 0
```

## Bootstrap

```bash
export GITHUB_PAT='<token-with-repo-scope>'
bash scripts/setup_github_manifests_secret.sh
bash scripts/push_fleet_manifests_to_github.sh
```
