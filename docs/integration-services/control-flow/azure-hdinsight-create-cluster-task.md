---
title: "Azure HDInsight créer des tâches de Cluster | Documents Microsoft"
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpcreatecltask.f1
- sql14.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 71a24dc15253916c32b07e6024e2ab32514c9d39
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-create-cluster-task"></a>Tâche de création d’un cluster Azure HDInsight
Le **Azure tâche** permet à un package SSIS créer un cluster Azure HDInsight dans le groupe de ressources et d’abonnement Azure spécifié.
  
Le **Azure tâche** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]  
> - Création d’un nouveau cluster HDInsight peut prendre 10 ~ 20 minutes.  
> - Il existe un coût associé à la création et exécution d’un cluster Azure HDInsight. Consultez [tarification HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/) pour plus d’informations.  
  
Pour ajouter une **tâche de création de cluster Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de création de cluster Azure HDInsight** .  
  
Le tableau suivant fournit une description des champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Field**|**Description**|  
|AzureResourceManagerConnection|Sélectionnez un gestionnaire de connexions Azure Resource Manager existant ou créez-en un qui permet de créer le cluster HDInsight.|  
|AzureStorageConnection|Sélectionnez un gestionnaire de connexions Azure Storage existant ou créez-en un nouveau qui fait référence à un compte Azure Storage qui sera associé au cluster HDInsight.|
|ID d’abonnement|Spécifiez l’ID de l’abonnement que sera créé dans le cluster HDInsight.|
|Groupe de ressources|Spécifiez la ressource Azure groupe cluster sera créé dans HDInsight.|
|Emplacement|Spécifiez l’emplacement du cluster HDInsight. Le cluster doit être créé dans le même emplacement que le compte de stockage Azure spécifié.|  
|ClusterName|Spécifiez un nom pour le cluster HDInsight à créer.|  
|ClusterSize|Spécifiez le nombre de nœuds pour créer le cluster.|  
|BlobContainer|Spécifiez le nom du conteneur de stockage par défaut pour être associé au cluster HDInsight.|  
|UserName|Spécifiez le nom d’utilisateur à utiliser pour la connexion au cluster HDInsight.|  
|Mot de passe|Spécifiez le mot de passe à utiliser pour la connexion au cluster HDInsight.|
|SshUserName|Spécifiez le nom d’utilisateur utilisé pour accéder à distance au cluster HDInsight à l’aide de SSH.|
|SshPassword|Spécifiez le mot de passe utilisé pour accéder à distance au cluster HDInsight à l’aide de SSH.|
|FailIfExists|Spécifiez si la tâche doit échouer si le cluster existe déjà.|  
  
> [!NOTE]  
> Les emplacements du cluster HDInsight et le compte de stockage Azure doivent être identiques.

