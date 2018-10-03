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
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fe5d4d2b6475c8f46a7d47f3b8106772def6dfb7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689848"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque entrée du journal générée par les packages ou par leurs tâches et conteneurs lors de l'exécution. Cette table est créée dans la base de données msdb lorsque vous installez [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Si vous configurez la journalisation dans une autre base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une table sysssislog de ce format est créée dans la base de données spécifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] écrit des entrées de journalisation dans cette table **uniquement** lorsque les packages utilisent le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] module fournisseur d’informations.  
  
  
|Nom de colonne|Type de données|Description|  
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
|datacode|**Int**|Valeur entière facultative qui indique généralement le résultat de l'exécution du conteneur ou de la tâche.|  
|databytes|**image**|Tableau d'octets facultatif qui contient des informations supplémentaires.|  
|message|**nvarchar**|Description de l'événement et des informations associées à l'événement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
