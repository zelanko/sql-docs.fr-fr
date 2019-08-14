---
title: Configurer Minikube
titleSuffix: SQL Server big data clusters
description: Découvrez comment configurer Minikube pour les déploiements de clusters Big Data SQL Server 2019 (préversion) sur une seule machine.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6c2261b5cfbbe590c76ce410da4b95ee678a20b5
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958475"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>Configurer Minikube pour les déploiements de clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment configurer **Minikube** pour les déploiements de clusters Big Data SQL Server 2019 (préversion) sur une seule machine. Minikube est un outil qui facilite l’exécution de Kubernetes sur une même machine, comme un ordinateur portable ou un poste de travail. Minikube permet d’exécuter un cluster Kubernetes à nœud unique dans une machine virtuelle de votre ordinateur portable. De cette façon, les utilisateurs peuvent essayer Kubernetes et développer avec au quotidien. 

## <a name="prerequisites"></a>Prérequis

- 32 Go de mémoire (64 Go sont recommandés).

- Si la machine ne dispose que de la quantité minimale de mémoire recommandée, configurez le déploiement du cluster pour qu’il ne comprenne qu’une seule instance de pool de calcul, une instance de pool de données et une instance de pool de stockage. Cette configuration ne doit être utilisée que pour les environnements d’évaluation où la durabilité et la disponibilité des données n’ont pas d’importance. Pour plus d’informations sur les variables d’environnement en vue de configurer des réplicas pour les pools de données, les pools de calcul et les pools de stockage, consultez la [documentation relative au déploiement](deployment-guidance.md#configfile).

- La virtualisation VT-x ou AMD-v doit être activée dans le BIOS de votre ordinateur.

## <a name="install-dependencies"></a>Installer des dépendances

1. Installez [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Installez Python 3 :
   - Si pip est manquant, téléchargez [get-clspip.py](https://bootstrap.pypa.io/get-pip.py), puis exécutez `python get-pip.py`.
   - Installez le package requests à l’aide de `python -m pip install requests`.

1. Si vous n’avez pas encore installé d’hyperviseur, installez-en un maintenant.
   - Pour OS X, installez [xhyve driver](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [VMware Fusion](https://www.vmware.com/products/fusion).
   - Pour Linux, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [KVM](https://www.linux-kvm.org/).
   - Pour Windows, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Si vous n’avez pas de commutateur externe configuré dans Hyper-V, créez-en un qui dispose d’un accès réseau externe.  Découvrez comment [créer un commutateur externe dans Hyper-V pour Minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Installer Minikube

Installez Minikube en suivant les instructions de la [version v0.28.2](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Le cluster Big Data SQL Server 2019 (préversion) fonctionne uniquement avec la version v0.24.1 et les versions ultérieures.

## <a name="create-a-minikube-cluster"></a>Créer un cluster Minikube

La commande ci-dessous crée un cluster Minikube dans une machine virtuelle Hyper-V avec 8 processeurs, 28 Go de mémoire et une taille de disque de 100 Go. La taille du disque ne correspond pas à un espace réservé.  Cela signifie simplement que cette taille peut être atteinte sur le disque en fonction des besoins.  Nous vous recommandons de ne pas configurer une taille inférieure à 100 Go, car d’après nos tests, cela engendre des problèmes. En outre, cela spécifie le commutateur Hyper-V avec un accès externe de manière explicite.

Modifiez les paramètres (par exemple, **--memory**) selon vos besoins, en fonction du matériel disponible et de l’hyperviseur que vous utilisez.  Vérifiez que le paramètre **--hyper-v** du commutateur virtuel correspond bien au nom que vous avez utilisé lors de la création du commutateur virtuel.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Si vous utilisez Minikube avec VirtualBox, la commande ressemble à ceci :

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Désactiver le point de contrôle automatique avec Hyper-V

Dans Windows 10, le point de contrôle automatique est activé sur une machine virtuelle. Exécutez la commande ci-dessous dans PowerShell pour désactiver le point de contrôle automatique sur la machine virtuelle.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Étapes suivantes

Les étapes décrites dans cet article configurent un cluster Minikube. L’étape suivante consiste à déployer le cluster Big Data SQL Server 2019. Pour obtenir des instructions, consultez l’article suivant :

[Déployer des clusters Big Data SQL Server 2019 sur Kubernetes](deployment-guidance.md#deploy)
