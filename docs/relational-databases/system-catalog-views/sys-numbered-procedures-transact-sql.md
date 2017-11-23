---
title: "fonctionnalité sys.numbered_procedures (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.numbered_procedures_TSQL
- numbered_procedures
- sys.numbered_procedures
- numbered_procedures_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.numbered_procedures catalog view
ms.assetid: 5b6d6498-bac6-4266-94b9-d16ef5089cf0
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e6a8dbd0f26b39c4fda367d2057cb9eb361586c5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysnumberedprocedures-transact-sql"></a>sys.numbered_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque procédure stockée SQL Server créée en tant que procédure numérotée, sauf pour la procédure stockée de base (numéro = 1). Entrées pour les procédures stockées de base sont accessibles dans les vues comme **sys.objects** et **sys.procedures**.  
  
> [!IMPORTANT]  
>  Les procédures numérotées ont été déconseillées. L'utilisation de procédures numérotées est déconseillée. Un événement DEPRECATION_ANNOUNCEMENT est déclenché lorsqu'une requête qui utilise cette vue de catalogue est compilée.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de l'objet de la procédure stockée.|  
|**procedure_number**|**smallint**|Numéro de cette procédure dans l'objet (supérieur ou égal à 2).|  
|**définition**|**nvarchar(max)**|Texte SQL Server qui définit cette procédure.<br /><br /> NULL = chiffré.|  
  
> [!NOTE]  
>  Les paramètres XML et CLR ne sont pas pris en charge pour les procédures numérotées.  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
