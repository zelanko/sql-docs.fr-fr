---
title: Sys.numbered_procedure_parameters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- numbered_procedure_parameters_TSQL
- sys.numbered_procedure_parameters_TSQL
- numbered_procedure_parameters
- sys.numbered_procedure_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.numbered_procedure_parameters catalog view
ms.assetid: a441d46d-1f30-41c2-8d94-e9442f59786e
author: stevestein
ms.author: sstein
ms.openlocfilehash: d07ca74ffb2b793038f230d2b3a5b265101a7eb8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102343"
---
# <a name="sysnumberedprocedureparameters-transact-sql"></a>sys.numbered_procedure_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par paramètre d'une procédure numérotée. Lorsque vous créez une procédure stockée numérotée, la procédure de base porte le numéro 1. Toutes les procédures suivantes portent les numéros 2, 3 et ainsi de suite. **Sys.numbered_procedure_parameters** contient les définitions de paramètres pour toutes les procédures suivantes, numérotées 2 et versions supérieures. Cette vue ne montre pas les paramètres de la procédure stockée de base (numéro 1) La procédure stockée de base est similaire à une procédure stockée non numérotée. Par conséquent, ses paramètres sont représentés dans [sys.parameters (Transact-SQL)](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md).  
  
> [!IMPORTANT]  
>  Les procédures numérotées ont été déconseillées. L'utilisation de procédures numérotées est déconseillée. Un événement DEPRECATION_ANNOUNCEMENT est déclenché lorsqu'une requête qui utilise cette vue de catalogue est compilée.  
  
> [!NOTE]  
>  Les paramètres XML et CLR ne sont pas pris en charge pour les procédures numérotées.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de l’objet auquel appartient ce paramètre.|  
|**procedure_number**|**smallint**|Numéro de cette procédure dans l'objet (supérieur ou égal à 2).|  
|**name**|**sysname**|Nom du paramètre. Est unique au sein de **procedure_number**.|  
|**parameter_id**|**Int**|ID du paramètre. Est unique au sein de la **procedure_number**.|  
|**system_type_id**|**tinyint**|ID du type de système du paramètre|  
|**user_type_id**|**Int**|ID du type, tel que défini par l'utilisateur, du paramètre.|  
|**max_length**|**smallint**|Longueur maximale du paramètre, en octets.<br /><br /> -1 = le type de données de colonne est varchar(max), nvarchar(max) ou varbinary(max).|  
|**precision**|**tinyint**|Précision du paramètre s'il est de type numérique ; sinon, 0.|  
|**scale**|**tinyint**|Échelle du paramètre s'il est de type numérique ; sinon, 0.|  
|**is_output**|**bit**|1 = le paramètre est un paramètre de sortie ou de retour ; sinon, 0|  
|**is_cursor_ref**|**bit**|1 = le paramètre est un paramètre de référence de curseur.|  
  
> [!NOTE]  
>  Les paramètres XML et CLR ne sont pas pris en charge pour les procédures numérotées.  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
