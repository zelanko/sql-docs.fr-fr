---
title: FILEPROPERTY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce71f17549cb286ed95004c62901337ce39c6739
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur de propriété de nom de fichier spécifiée lorsqu'un nom de fichier dans la base de données active et un nom de propriété sont fournis. Retourne NULL pour les fichiers qui ne figurent pas dans la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>Arguments  
 *nom_fichier*  
 Expression composée du nom du fichier associé à celui de la base de données actuelle dont les informations de propriété doivent être retournées. *file_name* est **nchar(128)**.  
  
 *propriété*  
 Expression contenant le nom de la propriété de fichier à renvoyer. *propriété* est **varchar (128)**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur| Description|Valeur retournée|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|Groupe de fichiers en lecture seule.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**IsPrimaryFile**|Le fichier est le fichier principal.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**IsLogFile**|Le fichier est un fichier journal.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Entrée non valide.|  
|**SpaceUsed**|Quantité d'espace occupé par le fichier spécifié.|Nombre de pages allouées dans le fichier.|  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 *file_name* correspond à la **nom** colonne dans la **sys.master_files** ou **sys.database_files** vue de catalogue.  
  
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
 [FILEGROUPPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
