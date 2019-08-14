---
title: Effectuer un déploiement avec un script bash sur un cluster kubeadm mononœud
titleSuffix: SQL Server big data clusters
description: Utilisez un script de déploiement bash pour déployer un cluster Big Data SQL Server 2019 (préversion) sur un cluster kubeadm mononœud.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 37017221b636146a003f8af8890c655ed605bca9
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68473071"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Effectuer un déploiement avec un script bash sur un cluster kubeadm mononœud

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dans ce tutoriel, vous utilisez un exemple de script de déploiement bash pour déployer un cluster Kubernetes mononœud à l’aide de kubeadm et un cluster Big Data SQL Server sur ce cluster.  

## <a name="prerequisites"></a>Conditions préalables requises

- Une machine virtuelle **serveur** Ubuntu 18.04 ou 16.04, version vanilla. Toutes les dépendances sont définies par le script et vous exécutez le script à partir de la machine virtuelle.

  > [!NOTE]
  > L’utilisation de machines virtuelles Azure n’est pas encore prise en charge.

- La machine virtuelle doit avoir au moins 8 UC, 64 Go de RAM et 100 Go d’espace disque. Après avoir tiré (pull) toutes les images Docker du cluster Big Data, vous disposez de 50 Go pour les données et les journaux à utiliser sur tous les composants.

## <a name="instructions"></a>Instructions

1. Téléchargez le script sur la machine virtuelle que vous prévoyez d’utiliser pour le déploiement.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Rendez le script exécutable avec la commande suivante.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Exécutez le script avec **sudo**.

   ```bash
   sudo ./setup-bdc.sh
   ```

   Quand vous y êtes invité, indiquez le mot de passe à utiliser pour les points de terminaison externes suivants : contrôleur, maître SQL Server et passerelle. Le nom d’utilisateur du contrôleur est *admin* par défaut.

4. Configurez un alias pour l’outil **azdata**.

   ```bash
   source ~/.bashrc
   ```

5. Vérifiez que l’alias fonctionne.

   ```bash
   azdata --version
   ```

## <a name="next-steps"></a>Étapes suivantes

Suivez [ce tutoriel](tutorial-load-sample-data.md) pour commencer à utiliser le cluster Big Data.
