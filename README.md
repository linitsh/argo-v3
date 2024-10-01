---
title     : 
tags      : []
categories: []
---
---
### ArgoCD Applications per EKS Cluster

Name of the folder represent name of the EKS Cluster (Except HelmCharts).

```
infra_repo                          # Devops repo
│
├── apps                            # Charts and Kustomize &apps
│   ├── chart-01                    # Base chart app
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
├── clusters                        # list of clusters for *apps
│   ├── cluster-01                  # EKS Cluster name
│   │   ├── bootstrap               # Cluster starup
│   │   └── environments                    # Inner cluster envs
│   │       ├── environment-01              # Specific environment
│   │       │   ├── applications            # ArgoCd applications specific environment (charts values, kustomizations)
│   │       │   │   ├── chart-01.yaml
│   │       │   │   ├── chart-xx.yaml
│   │       │   │   ├── kustomize-01.yaml
│   │       │   │   ├── kustomize-xx.yaml
│   │       │   │   └── ...
│   │       │   ├── overlays                    # Overlays for apps
│   │       │   │   ├── chart-01                # Same names like in apps
│   │       │   │   │   └── values.yaml         # Chart values for specific environment
│   │       │   │   ├── chart-xx
│   │       │   │   ├── kustomize-01
│   │       │   │   │   ├── kustomization.yaml  # Overlay of app for specific environment
│   │       │   │   │   └── ...
│   │       │   │   └── kustomize-xx
│   │       │   └── root.yaml
│   │       ├── environment-xx
│   │       └── ...
│   ├── cluster-xx
│   └── ...
│
├── control                 # Scripts / Tasks for control this repo
│   ├── scripts
│   │   ├── script-01.sh
│   │   └── script-02.sh
│   └── taskfile.yaml       # Root taskfile
│
├── docs
└── README.md
```

Copyleft (c) by LinitSH.