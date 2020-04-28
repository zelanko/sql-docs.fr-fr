---
title: Core. sp_create_snapshot (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_snapshot
- sp_create_snapshot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- management data warehouse, data collector stored procedures
- data collector [SQL Server], stored procedures
- core.sp_create_snapshot stored procedure
- sp_create_snapshot
ms.assetid: ff297bda-0ee2-4fda-91c8-7000377775e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef2bce1ff84172d01b1304a416f84865f1cb36bb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68078219"
---
# <a name="coresp_create_snapshot-transact-sql"></a>core.sp_create_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Insère une ligne dans la vue core.snapshots de l'entrepôt de données de gestion. Cette procédure est appelée chaque fois qu'un package de téléchargement commence à télécharger des données dans l'entrepôt de données de gestion.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
core.sp_create_snapshot [ @collection_set_uid = ] 'collection_set_uid'  
    , [ @collector_type_uid = ] 'collector_type_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @log_id = ] log_id  
    , [ @snapshot_id = ] snapshot_id OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [ @collection_set_uid = ] '*collection_set_uid*'  
 GUID du jeu d'éléments de collecte. *collection_set_uid* est de type **uniqueidentifier** et n’a pas de valeur par défaut. Pour obtenir le GUID, interrogez la vue dbo.syscollector_collection_sets dans la base de données msdb.  
  
 [ @collector_type_uid = ] '*collector_type_uid*'  
 GUID d'un type de collecteur. *collector_type_uid* est de type **uniqueidentifier** et n’a pas de valeur par défaut. Pour obtenir le GUID, interrogez la vue dbo.syscollector_collector_types dans la base de données msdb.  
  
 [ @machine_name= ] '*machine_name*'  
 Nom du serveur sur lequel réside le jeu d'éléments de collecte. *machine_name* est de **type sysname**, sans valeur par défaut.  
  
 [ @named_instance= ] '*named_instance*'  
 Nom de l'instance pour le jeu d'éléments de collecte. *named_instance* est de **type sysname**, sans valeur par défaut.  
  
 [ @log_id = ] *log_id*  
 Identificateur unique mappé au journal des événements de jeu d'éléments de collecte sur le serveur qui a collecté les données. *log_id* est de type **bigint** sans valeur par défaut. Pour obtenir la valeur de *log_id*, interrogez la vue dbo. syscollector_execution_log dans la base de données msdb.  
  
 [ @snapshot_id = ] *snapshot_id*  
 Identificateur unique d’une ligne qui est insérée dans la vue Core. snapshots. *snapshot_id* est de **type int** et est retourné en tant que sortie.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Chaque fois qu'un package de téléchargement commence à télécharger des données dans l'entrepôt de données de gestion, le composant runtime du collecteur de données appelle core.sp_create_snapshot.  
  
 Cette procédure vérifie les points suivants :  
  
-   collection_set_uid correspond à une entrée existante dans la table core.source_info_internal.  
  
-   collector_type_uid correspond à une entrée existante dans la vue core.supported_collector_types.  
  
 Si l'une des vérifications précédentes échoue, la procédure échoue et retourne une erreur.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle de base de données fixe **mdw_writer** (avec autorisation EXECUTE).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée un instantané pour le jeu d'éléments de collecte Utilisation du disque, l'ajoute à l'entrepôt de données de gestion, puis retourne l'identificateur de l'instantané. Dans l'exemple, l'instance par défaut est utilisée.  
  
```  
USE <management_data_warehouse>;  
DECLARE @snapshot_id int;  
EXEC core.sp_create_snapshot   
    @collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
    @collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @machine_name = '<computername>',  
    @named_instance = 'MSSQLSERVER',  
    @log_id = 11, -- ID of the log for the collection set  
    @snapshot_id = @snapshot_id OUTPUT;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [entrepôt de données de gestion](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
