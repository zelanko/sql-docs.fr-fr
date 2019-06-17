---
title: Enregistrements SQL Server Audit | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audit records [SQL Server]
ms.assetid: 7a291015-df15-44fe-8d53-c6d90a157118
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3cc249ebfce796d7932e68d993ac98ede867845f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63238389"
---
# <a name="sql-server-audit-records"></a>SQL Server Audit Records
  La fonctionnalité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit vous permet d'effectuer l'audit d'événements et de groupes d'événements au niveau du serveur et au niveau de la base de données. Pour plus d’informations, consultez [SQL Server Audit &#40;moteur de base de données&#41;](sql-server-audit-database-engine.md). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Les audits sont constitués de zéro ou plusieurs éléments d'action d'audit, enregistrés dans une *cible*d'audit. La cible d'audit peut être un fichier binaire, le journal des événements d'applications de Windows ou le journal des événements de sécurité de Windows. Les enregistrements envoyés à la cible peuvent contenir les éléments décrits dans le tableau suivant.  
  
|Nom de colonne|Description|type|Toujours disponible|  
|-----------------|-----------------|----------|----------------------|  
|**event_time**|Date/heure auxquelles l'action pouvant être auditée est déclenchée.|`datetime2`|Oui|  
|**sequence_no**|Assure le suivi de la séquence d'enregistrements dans un enregistrement d'audit unique qui était trop grand pour la mémoire tampon d'écriture pour audits.|`int`|Oui|  
|**action_id**|ID de l'action<br /><br /> Conseil : Pour utiliser **action_id** en tant que prédicat doit être converti à partir d’une chaîne de caractères en valeur numérique. Pour plus d’informations, consultez [Filtrage de l’audit SQL Server sur le prédicat action_id/class_type](https://blogs.msdn.com/b/sqlsecurity/archive/2012/10/03/filter-sql-server-audit-on-action-id-class-type-predicate.aspx).|`varchar(4)`|Oui|  
|**succeeded**|Indique si l'action qui a déclenché l'événement a réussi.|`bit` -1 = succès, 0 = Échec|Oui|  
|**permission_bitmask**|Le cas échéant, affiche les autorisations accordées, refusées ou révoquées.|`bigint`|Non|  
|**is_column_permission**|Indicateur qui désigne une autorisation au niveau colonne|`bit` -1 = Vrai, 0 = False|Non|  
|**session_id**|ID de la session au cours de laquelle l'événement s'est produit.|`int`|Oui|  
|**server_principal_id**|ID du contexte de connexion dans lequel l'action est effectuée.|`int`|Oui|  
|**database_principal_id**|ID du contexte de l'utilisateur de base de données dans lequel l'action est effectuée.|`int`|Non|  
|**object_id**|ID principal de l'entité sur laquelle l'audit s'est produit. Cela inclut :<br /><br /> les objets de serveur ;<br /><br /> Des bases de données<br /><br /> Des objets de base de données<br /><br /> les objets de schéma ;|`int`|Non|  
|**target_server_principal_id**|Principal du serveur auquel s'applique l'action pouvant être auditée.|`int`|Oui|  
|**target_database_principal_id**|Principal de la base de données auquel s'applique l'action pouvant être auditée.|`int`|Non|  
|**class_type**|Type d'entité pouvant être auditée sur laquelle l'audit se produit.|`varchar(2)`|Oui|  
|**session_server_principal_name**|Principal du serveur pour la session.|`sysname`|Oui|  
|**server_principal_name**|Connexion actuelle.|`sysname`|Oui|  
|**server_principal_sid**|SID de la connexion actuelle.|`varbinary`|Oui|  
|**database_principal_name**|Utilisateur actuel.|`sysname`|Non|  
|**target_server_principal_name**|Connexion cible de l'action.|`sysname`|Non|  
|**target_server_principal_sid**|SID de la connexion cible.|`varbinary`|Non|  
|**target_database_principal_name**|Utilisateur cible de l'action.|`sysname`|Non|  
|**server_instance_name**|Nom de l'instance de serveur où l'audit s'est produit. Utilise le format standard ordinateur\instance.|`nvarchar(120)`|Oui|  
|**database_name**|Contexte de base de données dans lequel l'action s'est produite.|`sysname`|Non|  
|**schema_name**|Contexte de schéma dans lequel l'action s'est produite.|`sysname`|Non|  
|**object_name**|Nom de l'entité sur laquelle l'audit s'est produit. Cela inclut :<br /><br /> les objets de serveur ;<br /><br /> Des bases de données<br /><br /> Des objets de base de données<br /><br /> Des objets de schéma<br /><br /> l'instruction TSQL (le cas échéant).|`sysname`|Non|  
|**instruction**|l'instruction TSQL (le cas échéant).|`nvarchar(4000)`|Non|  
|**additional_information**|Toute information supplémentaire à propos de l'événement, stockée au format XML.|`nvarchar(4000)`|Non|  
  
## <a name="remarks"></a>Notes  
 Certaines actions ne remplissent pas la valeur d'une colonne car elles peuvent ne pas être applicables à l'action.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit stocke 4000 caractères de données pour les champs de type caractère dans un enregistrement d'audit. Lorsque les valeurs **additional_information** et **statement** retournées à partir d’une action pouvant être auditée retournent plus de 4 000 caractères, la colonne **sequence_no** est utilisée pour écrire plusieurs enregistrements dans le rapport d’audit pour une action d’audit unique afin d’enregistrer ces données. Le processus est le suivant :  
  
-   La colonne **statement** est divisée en 4000 caractères.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit écrit sur la première ligne de l'enregistrement d'audit les données partielles. Tous les autres champs sont dupliqués sur chaque ligne.  
  
-   La valeur **sequence_no** est incrémentée.  
  
-   Ce processus est répété jusqu'à ce que toutes les données soient enregistrées.  
  
 Vous pouvez connecter les données en lisant séquentiellement les lignes à l’aide de la valeur **sequence_no** et des colonnes **event_Time**, **action_id** et **session_id** pour identifier l’action.  
  
## <a name="related-content"></a>Contenu associé  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql)  
  
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)  
  
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-audit-transact-sql)  
  
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql)  
  
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-audit-transact-sql)  
  
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)  
  
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-audit-specification-transact-sql)  
  
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)  
  
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)  
  
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)  
  
 [sys.server_audits &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)  
  
 [sys.server_file_audits &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)  
  
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)  
  
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)  
  
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)  
  
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)  
  
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)  
  
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)  
  
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)  
  
  
