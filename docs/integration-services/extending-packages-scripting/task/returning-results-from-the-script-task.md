---
title: Retour de résultats de la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 59a9ce64016cb4a3b748b504895262bce6be58d5
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65724049"
---
# <a name="returning-results-from-the-script-task"></a>Retour de résultats de la tâche de script

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La tâche de script utilise la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> et la propriété facultative <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> pour renvoyer des informations d'état à l'exécution [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], lesquelles peuvent être utilisées pour déterminer le chemin d'accès du flux de travail une fois que la tâche de script est terminée.  
  
## <a name="taskresult"></a>TaskResult  
 La propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> indique si la tâche a réussi ou a échoué. Par exemple :  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a>ExecutionValue  
 La propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> renvoie facultativement un objet défini par l'utilisateur qui quantifie ou fournit des informations supplémentaires sur le succès ou l'échec de la tâche de script. Par exemple, la tâche FTP utilise la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> pour renvoyer le nombre de fichiers transférés. La tâche d'exécution SQL renvoie le nombre de lignes affectées par la tâche. La propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> peut également servir à déterminer le chemin d'accès du flux de travail. Par exemple :  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
