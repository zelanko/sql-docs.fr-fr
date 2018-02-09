---
title: Sys.syscomments (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscomments_TSQL
- syscomments
- syscomments_TSQL
- sys.syscomments
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscomments compatibility view
- syscomments system table
ms.assetid: 767dd410-6bc9-4c4a-ab0f-6d2cf6163426
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9a49d0a12cbf6e8f0c07cf6913786a0b437f1d0a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des entrées pour chaque vue, règle, valeur par défaut, déclencheur, contrainte CHECK, contrainte DEFAULT et procédure stockée dans la base de données. Le **texte** colonne contient les instructions de définition SQL d’origine.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Nous vous recommandons d’utiliser à la place sys.sql_modules. Pour plus d’informations, consultez [sys.sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identificateur de l'objet auquel ce texte s'applique|  
|**number**|**smallint**|Numéro dans le groupe de procédures, si la procédure est groupée.<br /><br /> 0 = les entrées ne sont pas des procédures.|  
|**colid**|**smallint**|Numéro de séquence de ligne pour les définitions d'objet qui dépassent 4 000 caractères|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ctext**|**varbinary(8000)**|Octets bruts de l'instruction de définition SQL.|  
|**texttype**|**smallint**|0 = Commentaire fourni par l'utilisateur<br /><br /> 1 = Commentaire fourni par le système<br /><br /> 4 = Commentaire chiffré|  
|**language**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**encrypted**|**bit**|Indique si la définition de procédure est obscurcie.<br /><br /> 0 = Non obscurci<br /><br /> 1 = Obscurci<br /><br /> **\*\*Important \* \***  pour obscurcir les définitions de procédure stockée, utilisez CREATE PROCEDURE avec le mot clé de chiffrement.|  
|**compressed**|**bit**|Retourne toujours 0. Cette valeur indique que la procédure est compressée.|  
|**texte**|**nvarchar(4000)**|Texte intégral de l'instruction de définition SQL<br /><br /> La sémantique de l'expression décodée est équivalente au texte d'origine, par contre la syntaxe n'est pas garantie. Par exemple, les espaces sont supprimés de l'expression décodée.<br /><br /> Cela [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-vue compatible avec Obtient des informations en cours [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] structures et peut retourner plus de caractères que le **nvarchar (4000)** définition. **sp_help** retourne **nvarchar (4000)** en tant que type de données de la colonne de texte. Lorsque vous travaillez avec **syscomments** utilisez **nvarchar (max)**. Pour les nouveaux travaux de développement, n’utilisez pas **syscomments**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
