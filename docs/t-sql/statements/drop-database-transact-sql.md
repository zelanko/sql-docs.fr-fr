---
title: "DÉPLACER la base de données (Transact-SQL) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP DATABASE
- DROP_DATABASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], deleting
- removing databases
- database snapshots [SQL Server], removing
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- DROP DATABASE statement
- database removal [SQL Server], DROP DATABASE statement
ms.assetid: 477396a9-92dc-43c9-9b97-42c8728ede8e
caps.latest.revision: 83
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 6e1a96bb64c8cb6a81311f422d370e36d9489ca4
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="drop-database-transact-sql"></a>DROP DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Supprime un ou plusieurs bases de données utilisateur ou instantanés de base de données à partir d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- SQL Server Syntax  
DROP DATABASE [ IF EXISTS ] { database_name | database_snapshot_name } [ ,...n ] [;]  
```  
  
```  
-- Azure SQL Database, Azure SQL Data Warehouse and Parallel Data Warehouse Syntax   
DROP DATABASE database_name [;]  
```  
  
## <a name="arguments"></a>Arguments  
 *S’IL EXISTE*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Conditionnellement supprime la base de données uniquement s’il existe déjà.  
  
 *database_name*  
 Spécifie le nom de la base de données à supprimer. Pour afficher une liste des bases de données, utilisez la [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vue de catalogue.  
  
 *nom_instantané_base_de_données*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie le nom d'un instantané de base de données à supprimer.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Une base de données peut être supprimée quel que soit son statut : hors connexion, en lecture seule, suspect, etc. Pour afficher l’état actuel d’une base de données, utilisez la **sys.databases** vue de catalogue.  
  
 Une base de données supprimée ne peut être recréée que par la restauration d'une copie de sauvegarde. Les instantanés de base de données ne peuvent pas être sauvegardés et ne peuvent donc pas être restaurés.  
  
 Lorsqu’une base de données est supprimée, les [base de données master](../../relational-databases/databases/master-database.md) doivent être sauvegardées.  
  
 Si vous supprimez une base de données, celle-ci l'est également d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il en est de même pour les fichiers disque physiques utilisés par la base de données. Si la base de données ou l'un de ses fichiers est hors connexion lors de la suppression, les fichiers disque ne sont pas supprimés. Ces fichiers peuvent être supprimés manuellement à l'aide de l'Explorateur Windows. Pour supprimer une base de données à partir du serveur en cours sans supprimer les fichiers du système de fichiers, utilisez [sp_detach_db](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md).  
  
> [!WARNING]  
>  Suppression d’une base de données a FILE_SNAPSHOT les sauvegardes associées à elle réussira, mais les fichiers de base de données qui sont associés à des instantanés ne sont pas supprimés pour éviter l’invalidation de sauvegardes faisant référence à ces fichiers de base de données. Le fichier sera tronqué, mais n’est pas supprimé physiquement afin de conserver les sauvegardes FILE_SNAPSHOT. Pour plus d’informations, consultez [Sauvegarde et restauration SQL Server avec le service de stockage d’objets blob Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). **S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Si vous supprimez un instantané de base de données, celui-ci l'est également d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il en est de même pour les fichiers partiellement alloués du système de fichiers physiques NTFS utilisés par l'instantané. Pour plus d’informations sur l’utilisation des fichiers partiellement alloués par les instantanés de base de données, consultez [instantanés de base de données &#40; SQL Server &#41; ](../../relational-databases/databases/database-snapshots-sql-server.md). La suppression d'un instantané de base de données efface le cache de plan pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette opération entraîne la recompilation de tous les plans d'exécution ultérieurs et peut entraîner une baisse temporaire et brutale des performances des requêtes. Pour chaque mémoire cache effacée dans le cache de plan, le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient le message d'information suivant : « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a rencontré %d occurrence(s) de vidages de mémoire cache pour la mémoire cache '%s' (partie du cache du plan) en raison d'opérations de maintenance ou de reconfiguration de base de données ». Ce message est enregistré toutes les cinq minutes si le cache est vidé au cours de cet intervalle de temps.  
  
## <a name="interoperability"></a>Interopérabilité  
  
### <a name="sql-server"></a>SQL Server  
 Pour supprimer une base de données publiée à des fins de réplication transactionnelle, ou bien une base de données publiée ou abonnée à une réplication de fusion, vous devez d'abord supprimer sa réplication. Si une base de données est endommagée, si vous ne pouvez pas supprimer la réplication dans un premier temps ou si les deux cas de figure se présentent, vous pouvez toujours, dans la plupart des cas, supprimer la base de données à l'aide de l'instruction ALTER DATABASE pour la déconnecter, puis la supprimer.  
  
 Si la base de données intervient dans l'envoi de journaux, supprimez l'envoi de journaux avant de supprimer la base de données. Pour plus d’informations, consultez [À propos de la copie des journaux de transaction &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 [Bases de données système](../../relational-databases/databases/system-databases.md) ne peut pas être supprimé.  
  
 L'instruction DROP DATABASE doit être exécutée en mode autocommit et elle n'est pas autorisée dans une transaction implicite ou explicite. Le mode autocommit est le mode par défaut pour la gestion des transactions.  
  
 Vous ne pouvez pas supprimer une base de données en cours d'utilisation, c'est-à-dire ouverte par un utilisateur pour une opération de lecture ou d'écriture. Pour supprimer des utilisateurs de la base de données, utilisez ALTER DATABASE pour affecter à la base de données la valeur SINGLE_USER.  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Les instantanés de base de données doivent être supprimés avant que la base de données ne soit supprimée.  
  
 Suppression d’une activation de la base de données pour Stretch Database ne supprime pas les données distantes. Si vous souhaitez supprimer les données distantes, vous devez le supprimer manuellement.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 Vous devez être connecté à la base de données master pour supprimer une base de données.
  
 L'instruction DROP DATABASE doit être la seule instruction d'un traitement SQL et vous pouvez supprimer une seule base de données à la fois.
  
### [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
 Vous devez être connecté à la base de données master pour supprimer une base de données.
  
 L'instruction DROP DATABASE doit être la seule instruction d'un traitement SQL et vous pouvez supprimer une seule base de données à la fois.

## <a name="permissions"></a>Permissions  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Requiert le **contrôle** sur la base de données, ou **ALTER ANY DATABASE** autorisation ou l’appartenance au **db_owner** rôle de base de données fixe.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 Seuls la connexion du principal au niveau du serveur (créée par le processus de déploiement) ou les membres de la **dbmanager** du rôle de base de données peuvent supprimer une base de données.  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Requiert le **contrôle** sur la base de données, ou **ALTER ANY DATABASE** autorisation ou l’appartenance au **db_owner** rôle de base de données fixe.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-dropping-a-single-database"></a>A. Suppression d'une base de données unique  
 L'exemple suivant supprime la base de données `Sales`.  
  
```  
DROP DATABASE Sales;  
```  
  
### <a name="b-dropping-multiple-databases"></a>B. Suppression de plusieurs bases de données  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 L'exemple suivant supprime chacune des bases de données répertoriées.  
  
```  
DROP DATABASE Sales, NewSales;  
```  
  
### <a name="c-dropping-a-database-snapshot"></a>C. Suppression d'un instantané de base de données  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 L’exemple suivant supprime un instantané de base de données nommé `sales_snapshot0600`, sans affecter la base de données source.  
  
```  
DROP DATABASE sales_snapshot0600;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  

