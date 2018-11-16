---
title: Configurer Minikube pour les déploiements de cluster SQL Server 2019 big data | Microsoft Docs
description: Découvrez comment configurer Minikube pour les déploiements de cluster (version préliminaire) SQL Server 2019 big data sur un seul ordinateur.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 9b6902057c3bf5da706de8832b33c959ed285a9b
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51702347"
---
# <a name="configure-minikube-for-sql-server-2019-big-data-cluster-deployments"></a>Configurer Minikube pour les déploiements de cluster SQL Server 2019 big data

Cet article décrit comment configurer **minikube** sur un ordinateur unique pour les déploiements de cluster (version préliminaire) de SQL Server 2019 big data. Minikube est un outil qui facilite l’exécution de Kubernetes sur un seul ordinateur, comme un ordinateur portable ou un ordinateur de bureau. Minikube exécute un cluster Kubernetes à nœud unique à l’intérieur d’une machine virtuelle sur votre ordinateur portable pour les utilisateurs qui cherchent à essayer Kubernetes ou à développer avec quotidiennes. 

## <a name="prerequisites"></a>Prérequis

- Pour exécuter un cluster Minikube pour SQL Server 2019 CTP 2.1 dans une configuration de cluster SQL données volumineuses, il est recommandé que votre ordinateur soit au moins 32 Go de RAM.

   > [!TIP] 
   > Si l’ordinateur possède uniquement le minimum recommandé de mémoire, puis configurez le déploiement du cluster que 1 seule instance de pool de calcul, 1 instance de pool de données et instance de pool de stockage de 1. Cette configuration ne doit être utilisée pour les environnements d’évaluation où la durabilité et la disponibilité des données sont sans importance. Consultez le [documentation relative au déploiement](deployment-guidance.md#define-environment-variables) pour plus d’informations sur les variables d’environnement à définir pour configurer le nombre de réplicas pour les pools de données, de calcul, pools et les pools de stockage.

- La virtualisation x VT ou AMD-v doit être activée dans le BIOS de votre ordinateur.

## <a name="install-dependencies"></a>Installer les dépendances

1. Si pas déjà fait, installez git localement sur [Windows](https://git-for-windows.github.io/), [Linux ou Mac](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

1. Installer [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Installez Python 3 :
   - Si pip est manquant, téléchargez [get-clspip.py](https://bootstrap.pypa.io/get-pip.py) et exécutez `python get-pip.py`.
   - Demande d’installation à l’aide du package `python -m pip install requests`.

1. Si vous ne disposez pas d’un hyperviseur installé, installer une maintenant.
   - Pour OS X, vous devez installer [xhyve pilote](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads), ou [VMware Fusion](https://www.vmware.com/products/fusion).
   - Pour Linux, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [KVM](https://www.linux-kvm.org/).
   - Pour Windows, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Si vous n’avez pas d’un commutateur externe configuré dans hyper-v, créez-en un qui a accès au réseau externe.  Consultez Comment [créer le commutateur externe dans hyper-v pour minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Installer Minikube

Installer Minikube conformément aux instructions pour le [v0.28.2 version](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Le cluster de données volumineux de SQL Server 2019 CTP 2.1 fonctionne uniquement avec la version v0.24.1 et inscrire.

## <a name="create-a-minikube-cluster"></a>Créer un cluster Minikube

La commande suivante crée un cluster minikube dans une machine virtuelle Hyper-V dotée de 8 processeurs, 28 Go de mémoire, taille du disque de 100 Go. La taille du disque n’est pas un espace réservé.  Il atteint cette taille sur le disque en fonction des besoins.  Nous vous recommandons ne pas de modifier le disque de l’espace sur une valeur inférieure à 100 Go que nous avons rencontré des problèmes avec ce test. Il spécifie également le commutateur hyper-v avec un accès externe explicitement.

Modifier les paramètres tels que **--mémoire** en fonction des besoins en fonction de votre matériel et disponibles qui hyperviseur que vous utilisez.  Assurez-vous que le **--hyper-v** valeur du paramètre de commutateur virtuel correspond au nom que vous avez utilisé lors de la création de votre commutateur virtuel.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Si vous utilisez Minikube avec VirtualBox, la commande ressemblerait à ceci :

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Désactiver le point de contrôle automatique avec Hyper-V

Sur Windows 10, le point de contrôle automatique est activée sur une machine virtuelle. Exécutez la commande ci-dessous dans PowerShell pour désactiver le point de contrôle automatique sur la machine virtuelle.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Étapes suivantes

Les étapes décrites dans cet article configuré un cluster Minikube. L’étape suivante consiste à déployer le cluster de données volumineux de SQL Server 2019. Pour obtenir des instructions, consultez l’article suivant :

[Déployer SQL Server 2019 CTP 2.1 sur Kubernetes](deployment-guidance.md#deploy)
