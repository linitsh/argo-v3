---
title     : Test repository for ArgoCd
tags      : [argocd]
categories: [devops]
---
---
### ArgoCD App of Apps pattern

### Shema:
```
repo                                # Devops repo
│
├── apps                            # Charts and Kustomize apps
│   ├── chart-01                    # Base chart of app
│   │   ├── Chart.yaml
│   │   ├── templates
│   │   ├── values.yaml             # Default Chart Values
│   │   └── ...
│   ├── chart-xx
│   ├── kustomize-01                # Base kustomization app
│   │   ├── deployment.yaml
│   │   ├── kustomization.yaml
│   │   ├── service.yaml
│   │   └── ...
│   ├── kustomize-xx
│   └── ...
│   
├── clusters                        # List of clusters for apps
│   ├── cluster-01                  # Cluster name
│   │   ├── bootstrap                   # Cluster declarative creation
│   │   │   ├── terraform               # Can be any (Terraform, script etc...)
│   │   │   └── ...
│   │   └── environments                    # Inner cluster environments
│   │       ├── environment-01              # Specific environment
│   │       │   ├── applications            # ArgoCd applications for apps
│   │       │   │   ├── chart-01.yaml       # Same name as app
│   │       │   │   ├── chart-xx.yaml
│   │       │   │   ├── kustomize-01.yaml
│   │       │   │   ├── kustomize-xx.yaml
│   │       │   │   └── ...
│   │       │   ├── overlays                    # Overlays for apps
│   │       │   │   ├── chart-01                # Same name as app
│   │       │   │   │   └── values.yaml         # Chart values for specific environment
│   │       │   │   ├── chart-xx
│   │       │   │   ├── kustomize-01
│   │       │   │   │   ├── namespace.yaml      # Namespace same as environment name
│   │       │   │   │   ├── kustomization.yaml  # Overlay of app for specific environment
│   │       │   │   │   └── ...
│   │       │   │   ├── kustomize-xx
│   │       │   │   └── ...
│   │       │   └── root.yaml                   # Root App of Apps for specific environment
│   │       ├── environment-xx
│   │       └── ...
│   ├── cluster-xx
│   └── ...
│
├── control                 # Scripts / Tasks for control this repo
│   ├── scripts
│   │   ├── script-01.sh
│   │   ├── script-02.sh
│   │   └── ...
│   ├── tasks
│   └── taskfile.yaml       # Root taskfile
│
├── docs                    # Guides etc in markdown
│   ├── ...
│   │   ├── ...
│
└── README.md               # Root of doc
```

Copyleft (c) by LinitSH.