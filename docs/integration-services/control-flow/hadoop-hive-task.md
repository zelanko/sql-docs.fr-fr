---
title: Hive Hadoop, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadoophivetask.f1
ms.assetid: 10ff37c0-9f3f-442a-889b-c351afbdc74c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c78c8b091751e1fd849c3490544acd492cd595c
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58282893"
---
# <a name="hadoop-hive-task"></a>Tâche Hive Hadoop
  Utilisez la tâche Hive Hadoop pour exécuter le script Hive sur un cluster Hadoop.  
  
 Pour ajouter une tâche Hive Hadoop, sélectionnez-la et faites-la glisser vers le concepteur. Double-cliquez ensuite sur la tâche, ou cliquez avec le bouton droit et sélectionnez **Modifier**pour ouvrir la boîte de dialogue **Éditeur de tâches Hive Hadoop** .  
  
 ![Éditeur de tâches Hive Hadoop](../../integration-services/control-flow/media/hadoop-hive-task.png "Éditeur de tâches Hive Hadoop")  
  
## <a name="options"></a>Options  
 Configurez les options suivantes dans la boîte de dialogue **Éditeur de tâches Hive Hadoop** .  
  
|Champ|Description|  
|-----------|-----------------|  
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où le service WebHCat est hébergé.|  
|**SourceType**|Spécifiez le type de source de la requête. Les valeurs disponibles sont **ScriptFile** et **DirectInput**.|  
|**InlineScript**|Lorsque la valeur de **SourceType** est **DirectInput**, spécifiez le script Hive.|  
|**HadoopScriptFilePath**|Lorsque **SourceType** présente la valeur **ScriptFile**, spécifiez le chemin d’accès au fichier de script sur Hadoop.|  
|**TimeoutInMinutes**|Spécifiez une valeur de délai d’expiration en minutes. Le travail Hadoop s’arrête s’il ne s’est pas terminé avant la fin du délai d’expiration. Spécifiez 0 pour planifier une exécution asynchrone du travail Hadoop.|  
  
## <a name="see-also"></a> Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  
