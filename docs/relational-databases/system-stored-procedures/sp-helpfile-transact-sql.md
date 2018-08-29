---
title: sp_helpfile (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpfile
- sp_helpfile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfile
ms.assetid: 1546e0ae-5a99-4e01-9eb9-d147fa65884c
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74acb22b50ce918f070c817cb8954b46e47bb876
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023837"
---
# <a name="sphelpfile-transact-sql"></a>sp_helpfile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les noms physiques et les attributs des fichiers associés à la base de données active. Utilisez cette procédure stockée pour déterminer les noms des fichiers à associer ou à dissocier du serveur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpfile [ [ @filename= ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@filename =** ] **'***nom***'**  
 Nom logique des fichiers de la base de données active. *nom* est **sysname**, avec NULL comme valeur par défaut. Si *nom* est ne pas spécifié, les attributs de tous les fichiers dans la base de données en cours sont retournées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de fichier logique.|  
|**fileid**|**smallint**|Identificateur numérique du fichier. N’est pas renvoyée si *nom* est spécifié *.*|  
|**filename**|**NCHAR(260)**|Nom de fichier physique.|  
|**filegroup**|**sysname**|Groupe de fichiers auquel le fichier appartient.<br /><br /> NULL = Le fichier est un fichier journal. Ils ne font jamais partie d'un groupe de fichiers.|  
|**size**|**nvarchar(15)**|Taille du fichier en kilo-octets.|  
|**MaxSize**|**nvarchar(15)**|Taille maximale du fichier. La valeur UNLIMITED indique que le fichier peut augmenter jusqu'à ce que le disque soit plein.|  
|**Croissance**|**nvarchar(15)**|Incrément de croissance du fichier. Cela indique la quantité d’espace ajoutée au fichier chaque fois que ce nouvel espace est nécessaire.<br /><br /> 0 = La taille du fichier est fixe et n'augmente pas.|  
|**Utilisation**|**varchar (9)**|Pour le fichier de données, la valeur est **'données uniquement'** et pour le fichier journal est la valeur **journal uniquement**.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur les fichiers de [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfile;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Groupes de fichiers et fichiers de base de données](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
