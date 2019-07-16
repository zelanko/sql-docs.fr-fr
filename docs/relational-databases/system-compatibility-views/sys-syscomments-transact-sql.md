---
title: Sys.syscomments (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 183fa2fc1a674ec1cc987c265f5a0d4c399e27cc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010747"
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des entrées pour chaque vue, règle, valeur par défaut, déclencheur, contrainte CHECK, contrainte DEFAULT et procédure stockée dans la base de données. Le **texte** colonne contient les instructions SQL d’origine.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Nous vous recommandons d'utiliser à la place sys.sql_modules. Pour plus d’informations, consultez [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identificateur de l'objet auquel ce texte s'applique|  
|**nombre**|**smallint**|Numéro dans le groupe de procédures, si la procédure est groupée.<br /><br /> 0 = les entrées ne sont pas des procédures.|  
|**colid**|**smallint**|Numéro de séquence de ligne pour les définitions d'objet qui dépassent 4 000 caractères|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ctext**|**varbinary(8000)**|Octets bruts de l'instruction de définition SQL.|  
|**texttype**|**smallint**|0 = Commentaire fourni par l'utilisateur<br /><br /> 1 = Commentaire fourni par le système<br /><br /> 4 = Commentaire chiffré|  
|**language**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**encrypted**|**bit**|Indique si la définition de procédure est obscurcie.<br /><br /> 0 = Non obscurci<br /><br /> 1 = Obscurci<br /><br /> **\*\* Important \* \***  pour obscurcir les définitions de procédure stockée, utilisez CREATE PROCEDURE avec le mot clé de chiffrement.|  
|**compressed**|**bit**|Retourne toujours 0. Cette valeur indique que la procédure est compressée.|  
|**texte**|**nvarchar(4000)**|Texte intégral de l'instruction de définition SQL<br /><br /> La sémantique de l'expression décodée est équivalente au texte d'origine, par contre la syntaxe n'est pas garantie. Par exemple, les espaces sont supprimés de l'expression décodée.<br /><br /> Cela [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-vue compatible avec Obtient des informations à partir de l’actuel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] structures et peut retourner plus de caractères que le **nvarchar (4000)** définition. **sp_help** retourne **nvarchar (4000)** comme type de données de la colonne de texte. Lorsque vous travaillez avec **syscomments** envisager d’utiliser **nvarchar (max)** . Pour le développement, n’utilisez pas **syscomments**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
