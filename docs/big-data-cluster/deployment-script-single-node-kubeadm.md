---
title: Effectuer un déploiement avec un script bash sur un cluster kubeadm mononœud
titleSuffix: SQL Server big data clusters
description: Utilisez un script de déploiement bash pour déployer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] un sur un cluster kubeadm à nœud unique.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f6b6581eacad2fa9a65f64fdc29d6dfcde53852a
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652343"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Effectuer un déploiement avec un script bash sur un cluster kubeadm mononœud

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dans ce tutoriel, vous utilisez un exemple de script de déploiement bash pour déployer un cluster Kubernetes mononœud à l’aide de kubeadm et un cluster Big Data SQL Server sur ce cluster.  

## <a name="prerequisites"></a>Prérequis

- Une machine virtuelle ou physique de **serveur** Ubuntu 18,04 ou 16,04. Toutes les dépendances sont définies par le script et vous exécutez le script à partir de la machine virtuelle.

  > [!NOTE]
  > L’utilisation de machines virtuelles Linux Azure n’est pas encore prise en charge.

- La machine virtuelle doit avoir au moins 8 processeurs, 64 Go de RAM et 100 Go d’espace disque. Après avoir tiré (pull) toutes les images Docker du cluster Big Data, vous disposez de 50 Go pour les données et les journaux à utiliser sur tous les composants.

- Mettez à jour les packages existants à l’aide des commandes ci-dessous pour vous assurer que l’image du système d’exploitation est à jour.

   ``` bash
   sudo apt update&&apt upgrade -y
   sudo systemctl reboot
   ```

## <a name="recommended-virtual-machine-settings"></a>Paramètres d’ordinateur virtuel recommandés

1. Utilisez la configuration de la mémoire statique pour la machine virtuelle. Par exemple, dans les installations Hyper-V, n’utilisez pas l’allocation de mémoire dynamique, mais allouez la version recommandée de 64 Go ou plus.

1. Utilisez la fonctionnalité de point de contrôle ou d’instantané dans vos hyperviseurs afin de pouvoir restaurer l’ordinateur virtuel dans un état propre.


## <a name="instructions-to-deploy-sql-server-big-data-cluster"></a>Instructions pour déployer SQL Server Cluster Big Data

1. Téléchargez le script sur la machine virtuelle que vous prévoyez d’utiliser pour le déploiement.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Rendez le script exécutable avec la commande suivante.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Exécutez le script (Assurez-vous que vous êtes bien en cours d’exécution avec *sudo*)

   ```bash
   sudo ./setup-bdc.sh
   ```

   Quand vous y êtes invité, indiquez le mot de passe à utiliser pour les points de terminaison externes suivants : contrôleur, maître SQL Server et passerelle. Le mot de passe doit être suffisamment complexe en fonction des règles existantes pour SQL Server mot de passe. Le nom d’utilisateur du contrôleur est *admin* par défaut.

4. Configurez un alias pour l’outil **azdata**.

   ```bash
   source ~/.bashrc
   ```

5. Actualisation de l’alias pour azdata.

   ```bash
   azdata --version
   ```

## <a name="cleanup"></a>Nettoyer

Le script [Cleanup-BDC.sh](https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/cleanup-bdc.sh) est fourni comme commodité pour réinitialiser l’environnement si nécessaire. Toutefois, nous vous recommandons d’utiliser une machine virtuelle à des fins de test et d’utiliser la fonctionnalité d’instantané de votre hyperviseur pour restaurer l’ordinateur virtuel dans un état propre.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer à utiliser des clusters Big Data, consultez [le didacticiel: Chargez les exemples de données dans un](tutorial-load-sample-data.md)cluster SQL Server Big Data.
