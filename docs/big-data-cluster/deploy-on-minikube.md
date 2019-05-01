---
title: Configurer minikube
titleSuffix: SQL Server big data clusters
description: Découvrez comment configurer minikube pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data sur un seul ordinateur.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: afa5c3bae6eb7898ccaedf534382c9aeb467f01c
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473496"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>Configurer minikube pour les déploiements de cluster SQL Server big data

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment configurer **minikube** sur un ordinateur unique pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data. Minikube est un outil qui facilite l’exécution de Kubernetes sur un seul ordinateur, comme un ordinateur portable ou un ordinateur de bureau. Minikube exécute un cluster Kubernetes à nœud unique à l’intérieur d’une machine virtuelle sur votre ordinateur portable pour les utilisateurs qui cherchent à essayer Kubernetes ou à développer avec quotidiennes. 

## <a name="prerequisites"></a>Prérequis

- 32 Go de mémoire (64 Go recommandé).

- Si l’ordinateur possède uniquement le minimum recommandé de mémoire, puis configurez le déploiement du cluster que 1 seule instance de pool de calcul, 1 instance de pool de données et instance de pool de stockage de 1. Cette configuration ne doit être utilisée pour les environnements d’évaluation où la durabilité et la disponibilité des données sont sans importance. Consultez le [documentation relative au déploiement](deployment-guidance.md#configfile) pour plus d’informations sur les variables d’environnement à définir pour configurer le nombre de réplicas pour les pools de données, de calcul, pools et les pools de stockage.

- La virtualisation x VT ou AMD-v doit être activée dans le BIOS de votre ordinateur.

## <a name="install-dependencies"></a>Installer les dépendances

1. Installer [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Installez Python 3 :
   - Si pip est manquant, téléchargez [get-clspip.py](https://bootstrap.pypa.io/get-pip.py) et exécutez `python get-pip.py`.
   - Demande d’installation à l’aide du package `python -m pip install requests`.

1. Si vous ne disposez pas d’un hyperviseur installé, installer une maintenant.
   - Pour OS X, vous devez installer [xhyve pilote](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads), ou [VMware Fusion](https://www.vmware.com/products/fusion).
   - Pour Linux, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [KVM](https://www.linux-kvm.org/).
   - Pour Windows, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Si vous n’avez pas d’un commutateur externe configuré dans hyper-v, créez-en un qui a accès au réseau externe.  Consultez Comment [créer le commutateur externe dans hyper-v pour minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Installer minikube

Installer minikube conformément aux instructions pour le [v0.28.2 version](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Le cluster de données volumineuses de SQL Server 2019 (version préliminaire) fonctionne uniquement avec la version v0.24.1 et inscrire.

## <a name="create-a-minikube-cluster"></a>Créer un cluster minikube

La commande suivante crée un cluster minikube dans une machine virtuelle Hyper-V dotée de 8 processeurs, 28 Go de mémoire, taille du disque de 100 Go. La taille du disque n’est pas un espace réservé.  Il atteint cette taille sur le disque en fonction des besoins.  Nous vous recommandons ne pas de modifier le disque de l’espace sur une valeur inférieure à 100 Go que nous avons rencontré des problèmes avec ce test. Il spécifie également le commutateur hyper-v avec un accès externe explicitement.

Modifier les paramètres tels que **--mémoire** en fonction des besoins en fonction de votre matériel et disponibles qui hyperviseur que vous utilisez.  Assurez-vous que le **--hyper-v** valeur du paramètre de commutateur virtuel correspond au nom que vous avez utilisé lors de la création de votre commutateur virtuel.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Si vous utilisez minikube avec VirtualBox, la commande ressemblerait à ceci :

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Désactiver le point de contrôle automatique avec Hyper-V

Sur Windows 10, le point de contrôle automatique est activée sur une machine virtuelle. Exécutez la commande ci-dessous dans PowerShell pour désactiver le point de contrôle automatique sur la machine virtuelle.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Étapes suivantes

Les étapes décrites dans cet article configuré un cluster minikube. L’étape suivante consiste à déployer le cluster de données volumineux de SQL Server 2019. Pour obtenir des instructions, consultez l’article suivant :

[Déployer des clusters de données volumineuses de SQL Server 2019 sur Kubernetes](deployment-guidance.md#deploy)
