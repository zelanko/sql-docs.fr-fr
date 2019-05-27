---
title: FILE_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a2a2bbe6261d2a20e410fb12743751cb9203f32e
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65946106"
---
# <a name="fileid-transact-sql"></a>FILE_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Cette fonction retourne le numéro d’identification (ID) d’un fichier de composant de la base de données active à partir du nom logique donné.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FILE_ID ( file_name )  
```  
  
## <a name="arguments"></a>Arguments  
*file_name*  
Une expression de type **sysname**, représentant le nom logique du fichier dont `FILE_ID` retournera la valeur de l’ID.  
  
## <a name="return-types"></a>Types de retour  
**smallint**  
  
## <a name="remarks"></a>Notes   
*file_name* correspond au nom de fichier logique affiché dans la colonne Nom de l’affichage catalogue sys.master_files ou sys.database_files.  

`FILE_ID` retourne `NULL` si *file_name* ne correspond pas au nom logique d’un fichier de composant de la base de données active.
  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro d’identification de fichier assigné aux catalogues de texte intégral est supérieur à 32767. La fonction `FILE_ID` ayant un type de retour **smallint**, `FILE_ID` ne prendra pas en charge les fichiers de texte intégral. Utilisez plutôt [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
Cet exemple retourne la valeur d’ID du fichier `AdventureWorks_Data`, un fichier de composant de la base de données `ADVENTUREWORKS2012`.  

```sql  
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
  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités du moteur de base de données dépréciées dans SQL Server 2016](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [FILE_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/file-name-transact-sql.md)   
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
