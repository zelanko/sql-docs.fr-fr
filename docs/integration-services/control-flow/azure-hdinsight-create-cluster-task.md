---
title: "T&#226;che de cr&#233;ation d’un cluster Azure HDInsight | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpcreatecltask.f1"
  - "sql14.dts.designer.afpcreatecltask.f1"
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# T&#226;che de cr&#233;ation d’un cluster Azure HDInsight
  La **tâche de création d’un cluster Azure HDInsight** permet à un package SSIS de créer un cluster Azure HDInsight dans l’abonnement Azure spécifié.  
  
 La **tâche de création d’un cluster Azure HDInsight** est un composant de SQL Server Integration Services (SSIS) Feature Pack pour Azure pour SQL Server 2016. Le Feature Pack est disponible en téléchargement [ici](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  -   La création d’un nouveau cluster HDInsight prend généralement 10 minutes.  
> -   Il existe un coût associé à la création et à l’exécution d’un cluster Azure HDInsight. Consultez la rubrique [Tarification HDInsight](http://azure.microsoft.com/en-us/pricing/details/hdinsight/) pour plus d’informations.  
  
 Pour ajouter une **tâche de création de cluster Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de création de cluster Azure HDInsight**.  
  
 Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureSubscriptionConnection|Sélectionnez le gestionnaire de connexions d’un abonnement Azure existant ou créez-en un qui fait référence à un abonnement Azure qui héberge le cluster HDInsight.|  
|AzureStorageConnection|Sélectionnez un gestionnaire de connexions Azure Storage existant ou créez-en un nouveau qui fait référence à un compte Azure Storage qui sera associé au cluster HDInsight.|  
|Emplacement|Spécifiez l’emplacement du cluster HDInsight. Le cluster doit être créé au même emplacement que le stockage Azure.|  
|ClusterName|Spécifiez un nom pour le cluster HDInsight à créer.|  
|ClusterSize|Spécifiez le nombre de nœuds souhaité dans le cluster.|  
|BlobContainer|Spécifiez le nom du conteneur de stockage par défaut associé au cluster HDInsight.|  
|UserName|Spécifiez le nom de l’utilisateur qui a accès au cluster.|  
|Mot de passe|Spécifiez le mot de passe de l’utilisateur.|  
|FailIfExists|Spécifiez si la tâche doit échouer si le cluster existe déjà.|  
  
> [!NOTE]  
>  L’emplacement du cluster HDInsight et celui du stockage Azure doivent être identiques.  
  
  