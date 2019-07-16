---
title: sysssislog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d837049f36e4f7925f8e62a18987f51235f19c14
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029611"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque entrée du journal générée par les packages ou par leurs tâches et conteneurs lors de l'exécution. Cette table est créée dans la base de données msdb lorsque vous installez [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Si vous configurez la journalisation dans une autre base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une table sysssislog de ce format est créée dans la base de données spécifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] écrit des entrées de journalisation dans cette table **uniquement** lorsque les packages utilisent le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] module fournisseur d’informations.  
  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|id|**Int**|Identificateur unique de l'entrée d'enregistrement.|  
|événement|**sysname**|Nom de l'événement qui a généré l'entrée d'enregistrement.|  
|computer|**nvarchar**|Ordinateur sur lequel le package s'exécutait lors de la création de l'entrée d'enregistrement.|  
|operator|**nvarchar**|Nom de l'utilisateur qui a exécuté le package ayant créé l'entrée du journal.|  
|source|**nvarchar**|Nom de l'exécutable dans le package qui a généré l'entrée du journal.|  
|sourceid|**uniqueidentifier**|GUID de l'exécutable dans le package qui a généré l'entrée du journal.|  
|executionid|**uniqueidentifier**|GUID de l'instance d'exécution de l'exécutable qui a généré l'entrée du journal.|  
|starttime|**datetime**|L’heure que le package a commencé à exécuter.|  
|endtime|**datetime**|Heure de fin du package.<br /><br /> Cette fonctionnalité n'est pas implémentée. La valeur dans la colonne endtime est toujours identique à la valeur dans la colonne starttime.|  
|datacode|**int**|Valeur entière facultative qui indique généralement le résultat de l'exécution du conteneur ou de la tâche.|  
|databytes|**image**|Tableau d'octets facultatif qui contient des informations supplémentaires.|  
|message|**nvarchar**|Description de l'événement et des informations associées à l'événement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
