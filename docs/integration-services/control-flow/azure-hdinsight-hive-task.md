---
title: "T&#226;che Hive Azure HDInsight | Microsoft Docs"
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
  - "sql13.dts.designer.afphivetask.f1"
  - "sql14.dts.designer.afphivetask.f1"
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# T&#226;che Hive Azure HDInsight
  Utilisez la **tâche Hive Azure HDInsight** pour exécuter un script Hive sur un cluster Azure HDInsight.
     
Pour ajouter une **tâche Hive Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de tâches Hive Azure HDInsight**.  
  
 La **tâche Hive Azure HDInsight** est un composant de SQL Server Integration Services (SSIS) Feature Pack pour Azure pour SQL Server 2016. Le Feature Pack est disponible en téléchargement [ici](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
 La liste suivante décrit les champs de cette boîte de dialogue.  
  
1.  Dans le champ **AzureSubscriptionConnection** , sélectionnez le gestionnaire de connexions d’un abonnement Azure existant ou créez-en un qui fait référence à un abonnement Azure hébergeant le cluster HDInsight.  
  
2.  Dans le champ **HDInsightClusterName** , sélectionnez le nom du cluster HDInsight sur lequel vous souhaitez exécuter le script Hive.  
  
3.  Dans le champ **LocalLogFolder**, cliquez sur **... (points de suspension)** et sélectionnez le dossier dans lequel vous souhaitez télécharger les journaux de traitement Hive à partir du cluster HDInsight.  
  
4.  Deux méthodes permettent de spécifier le script Hive :  
  
    1.  **Script en ligne** : cliquez sur **... (points de suspension)** en regard du champ **Script**, puis retapez le script en ligne dans la boîte de dialogue **Entrer le script**.  
  
    2.  **Fichier de script**: téléchargez le fichier de script vers un emplacement d’objet blob et spécifiez son **BlobName**. Si l’objet blob ne se trouve pas dans le stockage ou le conteneur par défaut du cluster HDInsight, vous devez spécifier les paramètres **ExternalStorageAccountName** et **ExternalBlobContainer** . Dans le cas d’un objet blob externe, assurez-vous que cet objet est configuré comme étant accessible au public.  
  
     Si les deux sont spécifiés, le fichier de script sera utilisé ; le script en ligne est alors ignoré.  
  
  