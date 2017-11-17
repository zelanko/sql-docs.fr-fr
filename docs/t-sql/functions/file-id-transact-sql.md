---
title: FILE_ID (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- FILE_ID
- FILE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], files
- file IDs [SQL Server]
- FILE_ID function
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_ID
ms.assetid: 6a7382cf-a360-4d62-b9d2-5d747f56f076
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2544da5cb252b27f42a82e1fa400d7c28f503f20
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="fileid-transact-sql"></a>FILE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le numéro d'identification (ID) du fichier correspondant au nom du fichier logique donné dans la base de données actuelle.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FILE_ID ( file_name )  
```  
  
## <a name="arguments"></a>Arguments  
 *nom_fichier*  
 Est une expression de type **sysname** qui représente le nom du fichier pour lequel retourner l’ID de fichier.  
  
## <a name="return-types"></a>Types de retour  
 **smallint**  
  
## <a name="remarks"></a>Notes  
 *file_name* correspond au nom de fichier logique affiché dans la colonne de nom dans les affichages catalogue sys.master_files ou sys.database_files.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro d'identification de fichier assigné aux catalogues de texte intégral est supérieur à 32767. Étant donné que le type de retour de la fonction FILE_ID est **smallint**, cette fonction ne peut pas être utilisée pour les fichiers de recherche en texte intégral. Utilisez [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) à la place.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne l'ID du fichier `AdventureWorks_Data`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT FILE_ID('AdventureWorks2012_Data')AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités du moteur de base de données dépréciées dans SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Nom_fichier &#40; Transact-SQL &#41;](../../t-sql/functions/file-name-transact-sql.md)   
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

