---
title: sp_helpdb (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpdb
- sp_helpdb_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpdb
ms.assetid: 4c3e3302-6cf1-4b2b-8682-004049b578c3
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 365a72bec07a7da1dbec8e3fa695f60b314a273e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations sur une base de données précise ou sur toutes les bases de données.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@dbname=** ] **'***nom***'**  
 Nom de la base de données à propos de laquelle des informations sont transmises. *nom* est **sysname**, sans valeur par défaut. Si *nom* n’est pas spécifié, **sp_helpdb** des rapports sur toutes les bases de données dans le **sys.databases** vue de catalogue.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de la base de données.|  
|**DB_SIZE**|**nvarchar(13)**|Taille totale de la base de données.|  
|**propriétaire**|**sysname**|Base de données propriétaire, tel que **sa**.|  
|**dbid**|**smallint**|ID de la base de données.|  
|**créé**|**nvarchar(11)**|Date de création de la base de données.|  
|**status**|**nvarchar(600)**|Liste de valeurs, séparées par des virgules, d'options de base de données actuellement définies pour la base de données.<br /><br /> Les options définies par des valeurs booléennes ne sont affichées que si elles sont activées. Les options non booléennes sont répertoriées avec leurs valeurs correspondantes sous la forme de *option_name*=*valeur*.<br /><br /> Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).|  
|**COMPATIBILITY_LEVEL**|**tinyint**|Niveau de compatibilité de la base de données : 60, 65, 70, 80 ou 90.|  
  
 Si *nom* est spécifié, il est un jeu de résultats supplémentaire qui montre la répartition de fichier pour la base de données spécifié.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**NCHAR(128)**|Nom de fichier logique.|  
|**fileid**|**smallint**|ID de fichier.|  
|**nom de fichier**|**NCHAR(260)**|Nom de fichier du système d'exploitation (nom de fichier physique).|  
|**groupe de fichiers**|**nvarchar (128)**|Groupe de fichiers auquel le fichier appartient.<br /><br /> NULL = Il s'agit d'un fichier journal. Ils ne font jamais partie d'un groupe de fichiers.|  
|**taille**|**nvarchar(18)**|Taille du fichier exprimée en mégaoctets.|  
|**MaxSize**|**nvarchar(18)**|Taille maximale du fichier. La valeur UNLIMITED indique que le fichier peut augmenter jusqu'à ce que le disque soit plein.|  
|**croissance**|**nvarchar(18)**|Incrément de croissance du fichier. Cela indique la quantité d’espace ajoutée au fichier que chaque nouvel espace de temps est nécessaire.|  
|**utilisation**|**varchar (9)**|Utilisation du fichier. Pour un fichier de données, la valeur est **'données uniquement'** et du fichier journal de la valeur est **journal uniquement**.|  
  
## <a name="remarks"></a>Notes  
 Le **état** rapports quelles options ont été définies à ON dans la base de données du jeu de colonnes dans le résultat. Toutes les options de base de données ne sont pas signalées par le **état** colonne. Pour afficher une liste complète des paramètres de la base de données en cours, utilisez la **sys.databases** vue de catalogue.  
  
## <a name="permissions"></a>Permissions  
 Lorsqu’une base de données est spécifié, l’appartenance à la **public** rôle dans la base de données est nécessaire. Lorsqu’aucune base de données n’est spécifié, l’appartenance au **public** rôle dans le **master** base de données est requise.  
  
 Si une base de données ne sont pas accessibles, **sp_helpdb** affiche l’erreur message 15622 et autant d’informations sur la base de données que possible.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-information-about-a-single-database"></a>A. Renvoi d'informations sur une base de données unique  
 Cet exemple affiche des informations sur la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```tsql  
EXEC sp_helpdb N'AdventureWorks2012';  
```  
  
### <a name="b-returning-information-about-all-databases"></a>B. Renvoi d’informations sur toutes les bases de données  
 L'exemple ci-dessous affiche les informations relatives à toutes les bases de données installées sur le serveur sur lequel s'exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```tsql  
EXEC sp_helpdb;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [Sys.FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
