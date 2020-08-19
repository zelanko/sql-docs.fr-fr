---
description: Tâche Pig Hadoop
title: Hadoop Pig, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hadooppigtask.f1
ms.assetid: 90646316-9822-48aa-9900-295a33750780
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8bb1c648647ea2341e899989f6199cbacd583b1b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88393355"
---
# <a name="hadoop-pig-task"></a>Tâche Pig Hadoop

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Utilisez la tâche Pig Hadoop pour exécuter le script Pig sur un cluster Hadoop.  
  
 Pour ajouter une tâche Pig Hadoop, sélectionnez-la et faites-la glisser vers le concepteur. Puis double-cliquez sur la tâche, ou cliquez avec le bouton droit et sélectionnez **Modifier**pour visualiser la boîte de dialogue **Éditeur de tâches Pig Hadoop** .  
  
 ![Éditeur de tâches Pig Hadoop](../../integration-services/control-flow/media/hadoop-pig-task.png "Éditeur de tâches Pig Hadoop")  
  
## <a name="options"></a>Options  
 Configurez les options suivantes dans la boîte de dialogue **Éditeur de tâches Pig Hadoop** .  
  
|Champ|Description|  
|-----------|-----------------|  
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où le service WebHCat est hébergé.|  
|**SourceType**|Spécifiez le type de source de la requête. Les valeurs disponibles sont **ScriptFile** et **DirectInput**.|  
|**InlineScript**|Lorsque **SourceType** présente la valeur **DirectInput**, spécifiez le script Pig.|  
|**HadoopScriptFilePath**|Lorsque **SourceType** présente la valeur **ScriptFile**, spécifiez le chemin d’accès au fichier de script sur Hadoop.|  
|**TimeoutInMinutes**|Spécifiez une valeur de délai d’expiration en minutes. Le travail Hadoop s’arrête s’il ne s’est pas terminé avant la fin du délai d’expiration. Spécifiez 0 pour planifier une exécution asynchrone du travail Hadoop.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  
