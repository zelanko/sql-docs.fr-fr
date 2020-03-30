---
title: FILEPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILEPROPERTY_TSQL
- FILEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- names [SQL Server], files
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTY function
- file names [SQL Server], FILEPROPERTY
ms.assetid: b82244ed-d623-431f-aa06-8017349d847f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79be8af32c13b9e910b94b40bd3c1bf9b2c0e2c5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68071404"
---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur de propriété de nom de fichier spécifiée lorsqu'un nom de fichier dans la base de données active et un nom de propriété sont fournis. Retourne NULL pour les fichiers qui ne figurent pas dans la base de données active.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>Arguments  
 *file_name*  
 Expression composée du nom du fichier associé à celui de la base de données actuelle dont les informations de propriété doivent être retournées. *file_name* est de type **nchar(128)** .  
  
 *property*  
 Expression contenant le nom de la propriété de fichier à renvoyer. *property* est de type **varchar(128)** et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|Valeur retournée|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Groupe de fichiers en lecture seule.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**IsPrimaryFile**|Le fichier est le fichier principal.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**IsLogFile**|Le fichier est un fichier journal.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**SpaceUsed**|Quantité d'espace occupé par le fichier spécifié.|Nombre de pages allouées dans le fichier.|  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 *file_name* correspond à la colonne **name** de la vue de catalogue **sys.master_files** ou **sys.database_files**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple retourne la valeur de la propriété `IsPrimaryFile` pour le nom du fichier `AdventureWorks_Data` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT FILEPROPERTY('AdventureWorks2012_Data', 'IsPrimaryFile')AS [Primary File];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Primary File   
-------------  
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [FILEGROUPPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
