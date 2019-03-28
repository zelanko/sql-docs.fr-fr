---
title: sp_helpfilegroup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a01132d30a293bca084669a733834c7d034048e4
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538181"
---
# <a name="sphelpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le nom et les attributs des groupes de fichiers associés à la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @filegroupname = ] 'name'` Est le nom logique des groupes de fichiers dans la base de données actuelle. *nom* est **sysname**, avec NULL comme valeur par défaut. Si *nom* n’est pas spécifié, tous les groupes de fichiers dans la base de données active sont répertoriées et uniquement le premier jeu de résultats dans la section jeux de résultats s’affiche.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**groupname**|**sysname**|Nom du groupe de fichiers|  
|**groupid**|**smallint**|Identificateur numérique du groupe de fichiers.|  
|**filecount**|**Int**|Nombre de fichiers appartenant au groupe de fichiers.|  
  
 Si *nom* est spécifié, une ligne pour chaque fichier dans le groupe de fichiers est retournée.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Nom logique du fichier dans le groupe de fichiers.|  
|**fileid**|**smallint**|Identificateur numérique du fichier.|  
|**filename**|**nchar(260)**|Nom physique du fichier, y compris le chemin d'accès du répertoire.|  
|**size**|**nvarchar(15)**|Taille du fichier en kilo-octets.|  
|**maxsize**|**nvarchar(15)**|Taille maximale du fichier.<br /><br /> Taille maximale que peut atteindre le fichier. La valeur UNLIMITED indique que le fichier peut augmenter jusqu'à ce que le disque soit plein.|  
|**growth**|**nvarchar(15)**|Incrément de croissance du fichier. Quantité d'espace ajoutée au fichier chaque fois que de l'espace supplémentaire est nécessaire.<br /><br /> 0 = La taille du fichier est fixe et n'augmente pas.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. Renvoi de tous les groupes de fichiers d'une base de données  
 L'exemple suivant renvoie des informations sur les groupes de fichiers dans la base de données exemple [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>B. Renvoi de tous les fichiers d'un groupe de fichiers  
 L'exemple suivant renvoie des informations sur tous les fichiers du groupe de fichiers `PRIMARY` dans la base de données exemple [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Groupes de fichiers et fichiers de base de données](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
