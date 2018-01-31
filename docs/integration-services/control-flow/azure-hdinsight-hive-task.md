---
title: "Hive Azure HDInsight, tâche | Microsoft Docs"
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
- sql13.dts.designer.afphivetask.f1
- sql14.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f26c9b682c49da83d77dffa38e79eb385a30ef00
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="azure-hdinsight-hive-task"></a>Tâche Hive Azure HDInsight
Utilisez la **tâche Hive Azure HDInsight** pour exécuter un script Hive sur un cluster Azure HDInsight.
     
Pour ajouter une **tâche Hive Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de tâches Hive Azure HDInsight** .  
  
La **tâche Hive Azure HDInsight** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 La liste suivante décrit les champs de cette boîte de dialogue.  
  
1.  Dans le champ **HDInsightConnection**, sélectionnez un gestionnaire de connexions Azure HDInsight existant ou créez-en un qui fait référence au cluster Azure HDInsight utilisé pour exécuter le script.
  
2.  Dans le champ **AzureStorageConnection**, sélectionnez un gestionnaire de connexions Stockage Azure existant ou créez-en un qui fait référence au compte Stockage Azure associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
 
3.  Dans le champ **BlobContainer**, spécifiez le nom du conteneur de stockage associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
  
4.  Dans le champ **LocalLogFolder**, spécifiez le dossier dans lequel seront téléchargés les journaux de sortie d’exécution de script et les journaux d’erreurs. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.   
  
5.  Deux méthodes permettent de spécifier le script Hive à exécuter :
  
    1.  **Script en ligne** : renseignez le champ **Script** en tapant en ligne le script à exécuter dans la boîte de dialogue **Entrer le script**.
  
    2.  **Fichier de script** : téléchargez le fichier de script dans Stockage Blob Azure et renseignez le champ **BlobName**. Si l’objet blob ne se trouve pas dans le compte ou le conteneur de stockage par défaut associé au cluster HDInsight, vous devez renseigner les champs **ExternalStorageAccountName** et **ExternalBlobContainer**. Dans le cas d’un objet blob externe, assurez-vous qu’il est configuré comme étant accessible au public.  
  
     Si les deux sont spécifiés, le fichier de script est utilisé et le script en ligne est ignoré.
