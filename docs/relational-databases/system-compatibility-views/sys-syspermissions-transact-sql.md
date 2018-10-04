---
title: Sys.syspermissions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syspermissions_TSQL
- syspermissions_TSQL
- sys.syspermissions
- syspermissions
dev_langs:
- TSQL
helpviewer_keywords:
- syspermissions system table
- sys.syspermissions compatibility view
ms.assetid: ba9a9a88-55d2-41a7-b09b-342e8b9a54c5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 20ac49b8da959732c54e912898b375c9175d546d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822567"
---
# <a name="syssyspermissions-transact-sql"></a>sys.syspermissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur les autorisations accordées et refusées aux utilisateurs, groupes et rôles dans la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|ID de l'objet pour les autorisations relatives à cet objet.<br /><br /> 0 = Autorisations sur une instruction.|  
|**Bénéficiaire**|**smallint**|ID de l'utilisateur, du groupe ou du rôle affecté par l'autorisation.|  
|**Fournisseur d’autorisations**|**smallint**|ID de l'utilisateur, du groupe ou du rôle qui a accordé ou refusé l'autorisation.|  
|**actadd**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**actmod**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SELECT**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selmod**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**updadd**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**updmod**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refadd**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refmod**|**varbinary(4000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
