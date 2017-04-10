---
title: "T&#226;che Supprimer un cluster Azure HDInsight | Microsoft Docs"
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
  - "sql13.dts.designer.afpdelcltask.f1"
  - "sql14.dts.designer.afpdelcltask.f1"
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# T&#226;che Supprimer un cluster Azure HDInsight
  La tâche **Supprimer un cluster Azure HDInsight** permet à un package SSIS de supprimer un cluster Azure HDInsight dans l’abonnement Azure spécifié.  
  
 La **tâche Supprimer un cluster Azure HDInsight** est un composant de SQL Server Integration Services (SSIS) Feature Pack pour Azure pour SQL Server 2016. Le Feature Pack est disponible en téléchargement [ici](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  La suppression d’un cluster HDInsight prend généralement 10 minutes.  
  
 Pour ajouter une **tâche de suppression de cluster Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de suppression de cluster Azure HDInsight**.  
  
 Le tableau suivant décrit les champs de la boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureSubscriptionConnection|Sélectionnez le gestionnaire de connexions d’un abonnement Azure existant ou créez-en un qui fait référence à un abonnement Azure qui héberge le cluster HDInsight.|  
|ClusterName|Spécifiez le nom du cluster à supprimer.|  
|FailIfNotExists|Spécifiez si la tâche doit échouer si le cluster n’existe pas.|  
  
  