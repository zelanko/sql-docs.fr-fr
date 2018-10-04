---
title: Pig Azure HDInsight, tâche | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afppigtask.f1
- sql11.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0b5f0fb11e7dc5395ddb64d1b68dd8ee96083d16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152969"
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
  
    1.  **Script en ligne** : renseignez le champ **Script** en tapant en ligne le script à exécuter dans la boîte de dialogue **Entrer le script**.
  
    2.  **Fichier de script** : téléchargez le fichier de script dans Stockage Blob Azure et renseignez le champ **BlobName**. Si l’objet blob ne se trouve pas dans le compte ou le conteneur de stockage par défaut associé au cluster HDInsight, vous devez renseigner les champs **ExternalStorageAccountName** et **ExternalBlobContainer**. Dans le cas d’un objet blob externe, assurez-vous qu’il est configuré comme étant accessible au public.  
  
     Si les deux sont spécifiés, le fichier de script est utilisé et le script en ligne est ignoré.
