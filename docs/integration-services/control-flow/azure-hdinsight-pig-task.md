---
title: Pig Azure HDInsight, tâche | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afppigtask.f1
- sql14.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3b07d792d2b73b6fd400835bbfe656bb02db8e18
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65727950"
---
# <a name="azure-hdinsight-pig-task"></a>Tâche Pig Azure HDInsight

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Utilisez la **tâche Pig Azure HDInsight** pour exécuter un script Pig sur un cluster Azure HDInsight.
     
Pour ajouter une **tâche Pig Azure HDInsight**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de tâches Pig Azure HDInsight** .  
  
La **tâche Pig Azure HDInsight** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 La liste suivante décrit les champs de cette boîte de dialogue.  
  
1.  Dans le champ **HDInsightConnection**, sélectionnez un gestionnaire de connexions Azure HDInsight existant ou créez-en un qui fait référence au cluster Azure HDInsight utilisé pour exécuter le script.
  
2.  Dans le champ **AzureStorageConnection**, sélectionnez un gestionnaire de connexions Stockage Azure existant ou créez-en un qui fait référence au compte Stockage Azure associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
 
3.  Dans le champ **BlobContainer**, spécifiez le nom du conteneur de stockage associé au cluster. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.
  
4.  Dans le champ **LocalLogFolder**, spécifiez le dossier dans lequel seront téléchargés les journaux de sortie d’exécution de script et les journaux d’erreurs. Celui-ci est nécessaire uniquement si vous souhaitez télécharger les journaux de sortie d’exécution de script et les journaux d’erreurs.   
  
5.  Deux méthodes permettent de spécifier le script Pig à exécuter :
  
    1.  **Script inline** : renseignez le champ **Script** en tapant directement le script à exécuter dans la boîte de dialogue **Entrer le script**.
  
    2.  **Fichier script** : chargez le fichier script dans le Stockage Blob Azure et renseignez le champ **BlobName**. Si l’objet blob ne se trouve pas dans le compte ou le conteneur de stockage par défaut associé au cluster HDInsight, vous devez renseigner les champs **ExternalStorageAccountName** et **ExternalBlobContainer**. Dans le cas d’un objet blob externe, assurez-vous qu’il est configuré comme étant accessible au public.  
  
     Si les deux sont spécifiés, le fichier de script est utilisé et le script en ligne est ignoré.
