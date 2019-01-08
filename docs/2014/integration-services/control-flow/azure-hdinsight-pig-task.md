---
title: Pig Azure HDInsight, tâche | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afppigtask.f1
- sql11.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 30340a873846e20911a7f14694f9602c17d960e8
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52749411"
---
# <a name="azure-hdinsight-pig-task"></a>Tâche Pig Azure HDInsight
Utilisez la **tâche Pig Azure HDInsight** pour exécuter un script Pig sur un cluster Azure HDInsight.
     
Pour ajouter une **tâche Pig Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de tâches Pig Azure HDInsight** .  
  
 La liste suivante décrit les champs de cette boîte de dialogue.  
  
1.  Dans le champ **HDInsightConnection**, sélectionnez un gestionnaire de connexions Azure HDInsight existant ou créez-en un qui fait référence au cluster Azure HDInsight utilisé pour exécuter le script.
  
2.  Dans le champ **AzureStorageConnection**, sélectionnez un gestionnaire de connexions Stockage Azure existant ou créez-en un qui fait référence au compte Stockage Azure associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
 
3.  Dans le champ **BlobContainer**, spécifiez le nom du conteneur de stockage associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
  
4.  Dans le champ **LocalLogFolder**, spécifiez le dossier dans lequel seront téléchargés les journaux de sortie d’exécution de script et les journaux d’erreurs. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.   
  
5.  Deux méthodes permettent de spécifier le script Pig à exécuter :
  
    1.  **Script en ligne**: Spécifiez le **Script** champ en tapant en ligne le script à exécuter dans le **entrer le Script** boîte de dialogue.
  
    2.  **Fichier de script**: Téléchargez le fichier de script vers le stockage Blob Azure et spécifiez le **BlobName** champ. Si l’objet blob ne se trouve pas dans le compte ou le conteneur de stockage par défaut associé au cluster HDInsight, vous devez renseigner les champs **ExternalStorageAccountName** et **ExternalBlobContainer**. Dans le cas d’un objet blob externe, assurez-vous qu’il est configuré comme étant accessible au public.  
  
     Si les deux sont spécifiés, le fichier de script est utilisé et le script en ligne est ignoré.
