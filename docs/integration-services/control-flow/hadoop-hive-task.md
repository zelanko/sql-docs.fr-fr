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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f157b2b802142f6f00b7a3e9ffb2596ef80f1773
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298257"
---
# <a name="hadoop-hive-task"></a>Tâche Hive Hadoop

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
  
  
