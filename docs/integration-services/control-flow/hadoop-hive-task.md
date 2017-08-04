---
title: "Tâche Hive Hadoop | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hadoophivetask.f1
ms.assetid: 10ff37c0-9f3f-442a-889b-c351afbdc74c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5bfd2e1fcda13aed2d95bed0ec780ff4d3372b94
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="hadoop-hive-task"></a>Tâche Hive Hadoop
  Utilisez la tâche Hive Hadoop pour exécuter le script Hive sur un cluster Hadoop.  
  
 Pour ajouter une tâche Hive Hadoop, sélectionnez-la et faites-la glisser vers le concepteur. Double-cliquez ensuite sur la tâche, ou cliquez avec le bouton droit et sélectionnez **Modifier**pour ouvrir la boîte de dialogue **Éditeur de tâches Hive Hadoop** .  
  
 ![Éditeur de tâches Hive Hadoop](../../integration-services/control-flow/media/hadoop-hive-task.png "Éditeur de tâches Hive Hadoop")  
  
## <a name="options"></a>Options  
 Configurez les options suivantes dans la boîte de dialogue **Éditeur de tâches Hive Hadoop** .  
  
|Champ|Description|  
|-----------|-----------------|  
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où se trouve le service WebHCat.|  
|**SourceType**|Spécifiez le type de source de la requête. Les valeurs disponibles sont **ScriptFile** et **DirectInput**.|  
|**InlineScript**|Lorsque la valeur de **SourceType** est **DirectInput**, spécifiez le script Hive.|  
|**HadoopScriptFilePath**|Lorsque **SourceType** présente la valeur **ScriptFile**, spécifiez le chemin d’accès au fichier de script sur Hadoop.|  
|**TimeoutInMinutes**|Spécifiez une valeur de délai d’expiration en minutes. Le travail Hadoop s’arrête s’il ne s’est pas terminé avant la fin du délai d’expiration. Spécifiez 0 pour planifier une exécution asynchrone du travail Hadoop.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  
