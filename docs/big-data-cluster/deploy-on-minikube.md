---
title: Configurer Minikube pour les déploiements de SQL Server 2019 CTP 2.0 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 1f20f2adc916a456e4a1975804fac1640ee95f69
ms.sourcegitcommit: 8aecafdaaee615b4cd0a9889f5721b1c7b13e160
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48818047"
---
# <a name="configure-minikube-for-sql-server-2019-ctp-20"></a>Configurer Minikube pour SQL Server 2019 CTP 2.0

Minikube est un outil qui facilite l’exécution de Kubernetes sur un seul ordinateur, comme un ordinateur portable ou un ordinateur de bureau. Minikube exécute un cluster Kubernetes à nœud unique à l’intérieur d’une machine virtuelle sur votre ordinateur portable pour les utilisateurs qui cherchent à essayer Kubernetes ou à développer avec quotidiennes. 

## <a name="prerequisites"></a>Prérequis

- Pour exécuter un cluster Minikube pour SQL Server 2019 CTP 2.0 dans une configuration de cluster SQL Big Data, il est recommandé que votre ordinateur soit au moins 32 Go de RAM.

   > [!TIP] 
   > Si l’ordinateur possède une mémoire insuffisante, puis modifier la configuration de cluster telles qu’uniquement 3 instances sont créées : une seule instance maître et deux instances de calcul.

- La virtualisation x VT ou AMD-v doit être activée dans le BIOS de votre ordinateur.

## <a name="install-dependencies"></a>Installer les dépendances

1. Si pas déjà fait, installez git localement sur [Windows](https://git-for-windows.github.io/), [Linux ou Mac](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

1. Installer [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Installez Python 3 :
   - Si pip est manquant, téléchargez [get-clspip.py](https://bootstrap.pypa.io/get-pip.py) et exécutez `python get-pip.py`.
   - Demande d’installation à l’aide du package `python -m pip install requests`.

1. Si vous ne disposez pas d’un hyperviseur installé, installer une maintenant.
   - Pour OS X, vous devez installer [xhyve pilote](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads), ou [VMware Fusion](https://www.vmware.com/products/fusion).
   - Pour Linux, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [KVM](http://www.linux-kvm.org/).
   - Pour Windows, installez [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ou [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Si vous n’avez pas d’un commutateur externe configuré dans hyper-v, créez-en un qui a accès au réseau externe.  Consultez Comment [créer le commutateur externe dans hyper-v pour minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Installer Minikube

Installer Minikube conformément aux instructions pour le [v0.28.2 version](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Le cluster de données volumineux de SQL Server 2019 CTP 2.0 fonctionne uniquement avec la version v0.24.1 et inscrire.

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

Les étapes décrites dans cet article configuré un cluster Minikube. L’étape suivante consiste à déployer SQL Server 2019 CTP 2.0 sur le cluster.

[Déployer SQL Server 2019 CTP 2.0 sur Kubernetes](deployment-guidance.md#deploy)
