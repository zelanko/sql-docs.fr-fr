---
title: Supprimer un cluster Azure HDInsight, tâche | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52147ff689b88876512afd6cb428e78c6c00d621
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913859"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Tâche Supprimer un cluster Azure HDInsight

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


La tâche **Supprimer un cluster Azure HDInsight** permet à un package SSIS de supprimer un cluster Azure HDInsight dans l’abonnement et le groupe de ressources Azure spécifiés.
  
La **tâche Supprimer un cluster Azure HDInsight** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]
> La suppression d’un cluster HDInsight peut prendre 10 à 20 minutes.  
  
Pour ajouter une **tâche de suppression de cluster Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de suppression de cluster Azure HDInsight** .  
  
Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureResourceManagerConnection|Sélectionnez un gestionnaire de connexions Azure Resource Manager existant ou créez-en un qui sera utilisé pour supprimer le cluster HDInsight.|
|SubscriptionId|Spécifiez l’ID de l’abonnement du cluster HDInsight.|
|ResourceGroup|Spécifiez le groupe de ressources Azure du cluster HDInsight.|
|ClusterName|Spécifiez le nom du cluster à supprimer.|  
|FailIfNotExists|Spécifiez si la tâche doit échouer si le cluster n’existe pas.|
