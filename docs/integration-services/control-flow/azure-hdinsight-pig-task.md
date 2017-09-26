---
title: "Tâche Pig Azure HDInsight | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afppigtask.f1
- sql14.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9874b119b634966b146f8fa9d22c016bcd91617b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-pig-task"></a>Tâche Pig Azure HDInsight
Utilisez la **tâche Pig Azure HDInsight** pour exécuter un script Pig sur un cluster Azure HDInsight.
     
Pour ajouter une **tâche Pig Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de tâches Pig Azure HDInsight** .  
  
Le **tâche Pig Azure HDInsight** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 La liste suivante décrit les champs de cette boîte de dialogue.  
  
1.  Pour le **HDInsightConnection** champ, sélectionnez un gestionnaire de connexions Azure HDInsight existant ou créez-en un qui fait référence à un cluster Azure HDInsight utilisé pour exécuter le script.
  
2.  Pour le **AzureStorageConnection** champ, sélectionnez un gestionnaire de connexions de stockage Azure existant ou créez-en un qui fait référence au compte de stockage Azure associé au cluster. Cela est uniquement nécessaire si vous souhaitez télécharger les journaux de sortie et de l’exécution du script.
 
3.  Pour le **BlobContainer** champ, spécifiez le nom de conteneur de stockage associé au cluster. Cela est uniquement nécessaire si vous souhaitez télécharger les journaux de sortie et de l’exécution du script.
  
4.  Pour le **LocalLogFolder** champ, spécifiez le dossier dans lequel les journaux de sortie et de l’exécution du script seront téléchargées sur. Cela est uniquement nécessaire si vous souhaitez télécharger les journaux de sortie et de l’exécution du script.   
  
5.  Il existe deux façons de spécifier le script Pig à exécuter :
  
    1.  **Script en ligne**: spécifiez le **Script** champ en tapant en ligne le script à exécuter dans le **entrer le Script** boîte de dialogue.
  
    2.  **Fichier de script**: Téléchargez le fichier de script pour le stockage d’objets Blob Azure et spécifiez le **BlobName** champ. Si l’objet blob n’est pas dans le compte de stockage par défaut ou le conteneur associé au cluster HDInsight, le **ExternalStorageAccountName** et **ExternalBlobContainer** champs doivent être spécifiés. Pour un objet blob externe, assurez-vous qu’il est configuré comme accessibles au public.  
  
     Si les deux sont spécifiées, le fichier de script sera utilisé et le script en ligne est ignoré.

