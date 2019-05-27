---
title: FILEGROUPPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILEGROUPPROPERTY_TSQL
- FILEGROUPPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], property values
- FILEGROUPPROPERTY function
- viewing filegroup properties
- displaying filegroup properties
ms.assetid: b3a930e6-df05-4034-929c-f681f5f6fc6e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ed5486e9f48bc0f0ca5ab4b6af031571f4f3580d
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945951"
---
# <a name="filegroupproperty-transact-sql"></a>FILEGROUPPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Cette fonction retourne la valeur de propriété du groupe de fichiers pour un nom spécifié et une valeur de groupe de fichiers.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FILEGROUPPROPERTY ( filegroup_name, property )  
```  
  
## <a name="arguments"></a>Arguments  
 *filegroup_name*  
Expression de type **sysname** représentant le nom du groupe de fichiers pour lequel `FILEGROUPPROPERTY` retourne les informations sur la propriété nommée.  
  
 *property*  
Expression de type **varchar(128)** qui retourne le nom de la propriété du groupe de fichiers. *property* peut retourner l’une des valeurs suivantes :  
  
|Valeur|Description|Valeur retournée|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Groupe de fichiers en lecture seule.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide.|  
|**IsUserDefinedFG**|Groupe de fichiers défini par l'utilisateur.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide.|  
|**IsDefault**|Groupe de fichiers par défaut.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide.|  
  
## <a name="return-types"></a>Types de retour  
**Int**  
  
## <a name="remarks"></a>Notes   
*filegroup_name* correspond à la colonne **name** de la vue de catalogue **sys.filegroups**.  
  
## <a name="examples"></a>Exemples  
Cet exemple retourne le paramètre de la propriété `IsDefault` relatif au groupe de fichiers principal de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT FILEGROUPPROPERTY('PRIMARY', 'IsDefault') AS 'Default Filegroup';  
GO  
```  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Default Filegroup   
---------------------   
1  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a> Voir aussi  
 [FILEGROUP_ID &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-id-transact-sql.md)   
 [FILEGROUP_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/filegroup-name-transact-sql.md)   
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)  
  
  
