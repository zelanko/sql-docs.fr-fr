---
description: Événements DDL
title: Événements DDL | Microsoft Docs
ms.custom: ''
ms.date: 11/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL events
- DDL triggers, events
- events [SQL Server], DDL
ms.assetid: 62ef24b4-3553-4aed-b62a-670980bae501
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 25cdef293ced7b58ea41f71f78a1046c6b5dd0ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463793"
---
# <a name="ddl-events"></a>Événements DDL
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Les tableaux suivants répertorient les événements DDL qui peuvent être utilisés pour activer une notification d'événements ou un déclencheur DDL. Notez que chaque événement correspond à une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ou à une procédure stockée, la syntaxe de l'instruction étant modifiée pour inclure un trait de soulignement (_) entre les mots clés.  
  
> [!IMPORTANT]  
>  Les procédures stockées système qui exécutent des opérations de type DDL peuvent également activer des notifications d'événements et des déclencheurs DDL. Testez vos déclencheurs et notifications d'événements DDL afin de déterminer leur réponse aux procédures stockées système qui sont exécutées. Par exemple, l’instruction CREATE TYPE et la procédure stockée **sp_addtype** activent toutes les deux un déclencheur ou une notification d’événements DDL créés sur un événement CREATE_TYPE.  
  
## <a name="ddl-statements-that-have-server-or-database-scope"></a>Instructions DDL qui ont une étendue à l'échelle du serveur ou de la base de données  
 Les déclencheurs ou les notifications d'événements DDL peuvent être créés de façon à se déclencher en réponse aux événements ci-dessous, lorsqu'ils se produisent dans la base de données dans laquelle le déclencheur ou la notification d'événement sont créés ou à un emplacement quelconque dans l'instance du serveur.  
  
:::row:::
    :::column:::
        CREATE_APPLICATION_ROLE (S’applique à l’instruction CREATE APPLICATION ROLE et à **sp_addapprole**. Si un nouveau schéma est créé, cet événement déclenche également un événement CREATE_SCHEMA.)
    :::column-end:::
    :::column:::
        ALTER_APPLICATION_ROLE (S’applique à l’instruction ALTER APPLICATION ROLE et à **sp_approlepassword**.)
    :::column-end:::
    :::column:::
        DROP_APPLICATION_ROLE (S’applique à l’instruction DROP APPLICATION ROLE et à **sp_dropapprole**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ASSEMBLY
    :::column-end:::
    :::column:::
        ALTER_ASSEMBLY
    :::column-end:::
    :::column:::
        DROP_ASSEMBLY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ASYMMETRIC_KEY
    :::column-end:::
    :::column:::
        ALTER_ASYMMETRIC_KEY
    :::column-end:::
    :::column:::
        DROP_ASYMMETRIC_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ALTER_AUTHORIZATION
    :::column-end:::
    :::column:::
        ALTER_AUTHORIZATION_DATABASE (S’applique à l’instruction ALTER AUTHORIZATION quand ON DATABASE est spécifié, ainsi qu’à **sp_changedbowner**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
    :::column:::
        CREATE_BROKER_PRIORITY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CERTIFICATE
    :::column-end:::
    :::column:::
        ALTER_CERTIFICATE
    :::column-end:::
    :::column:::
        DROP_CERTIFICATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CONTRACT
    :::column-end:::
    :::column:::
        DROP_CONTRACT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CREDENTIAL
    :::column-end:::
    :::column:::
        ALTER_CREDENTIAL
    :::column-end:::
    :::column:::
        DROP_CREDENTIAL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        GRANT_DATABASE
    :::column-end:::
    :::column:::
        DENY_DATABASE
    :::column-end:::
    :::column:::
        REVOKE_DATABASE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
    :::column:::
        ALTER_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
    :::column:::
        DENY_DATABASE_AUDIT_SPEFICIATION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE_ENCRYPTION_KEY
    :::column-end:::
    :::column:::
        ALTER_DATABASE_ENCRYPTION_KEY
    :::column-end:::
    :::column:::
        DROP_DATABASE_ENCRYPTION_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DEFAULT
    :::column-end:::
    :::column:::
        DROP_DEFAULT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        BIND_DEFAULT (S’applique à **sp_bindefault**.)
    :::column-end:::
    :::column:::
        UNBIND_DEFAULT (S’applique à **sp_unbindefault**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EVENT_NOTIFICATION
    :::column-end:::
    :::column:::
        DROP_EVENT_NOTIFICATION
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EXTENDED_PROPERTY (S’applique à **sp_addextendedproperty**.)
    :::column-end:::
    :::column:::
        ALTER_EXTENDED_PROPERTY (S’applique à **sp_updateextendedproperty**.)
    :::column-end:::
    :::column:::
        DROP_EXTENDED_PROPERTY (S’applique à **sp_dropextendedproperty**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_CATALOG (S’applique à l’instruction CREATE FULLTEXT CATALOG et à **sp_fulltextcatalog** quand *create* est spécifié.)
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_CATALOG (S’applique à l’instruction ALTER FULLTEXT CATALOG, à **sp_fulltextcatalog** quand *start_incremental*, *start_full*, *Stop*ou *Rebuild* est spécifié, et à **sp_fulltext_database** quand *enable* est spécifié.)
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_CATALOG (S’applique à l’instruction DROP FULLTEXT CATALOG et à **sp_fulltextcatalog** quand *drop* est spécifié.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_INDEX (S’applique à l’instruction CREATE FULLTEXT INDEX et à **sp_fulltexttable** quand *create* est spécifié.)
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_INDEX (S’applique à l’instruction ALTER FULLTEXT INDEX, à **sp_fulltextcatalog** quand *start_full*, *start_incremental*ou *stop* est spécifié, à **sp_fulltext_column**et **sp_fulltext_table** quand toute action autre que *create* ou *drop* est spécifiée.)
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_INDEX (S’applique à l’instruction DROP FULLTEXT INDEX et à **sp_fulltexttable** quand *drop* est spécifié.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FULLTEXT_STOPLIST
    :::column-end:::
    :::column:::
        ALTER_FULLTEXT_STOPLIST
    :::column-end:::
    :::column:::
        DROP_FULLTEXT_STOPLIST
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_FUNCTION
    :::column-end:::
    :::column:::
        ALTER_FUNCTION
    :::column-end:::
    :::column:::
        DROP_FUNCTION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX (S’applique à l’instruction ALTER INDEX et à **sp_indexoption**.)
    :::column-end:::
    :::column:::
        DROP_INDEX
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MASTER_KEY
    :::column-end:::
    :::column:::
        ALTER_MASTER_KEY
    :::column-end:::
    :::column:::
        DROP_MASTER_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MESSAGE_TYPE
    :::column-end:::
    :::column:::
        ALTER_MESSAGE_TYPE
    :::column-end:::
    :::column:::
        DROP_MESSAGE_TYPE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PARTITION_FUNCTION
    :::column-end:::
    :::column:::
        ALTER_PARTITION_FUNCTION
    :::column-end:::
    :::column:::
        DROP_PARTITION_FUNCTION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PARTITION_SCHEME
    :::column-end:::
    :::column:::
        ALTER_PARTITION_SCHEME
    :::column-end:::
    :::column:::
        DROP_PARTITION_SCHEME
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PLAN_GUIDE (S’applique à **sp_create_plan_guide**.)
    :::column-end:::
    :::column:::
        ALTER_PLAN_GUIDE (S’applique à **sp_control_plan_guide** quand ENABLE, ENABLE ALL, DISABLE ou DISABLE ALL est spécifié.)
    :::column-end:::
    :::column:::
        DROP_PLAN_GUIDE (S’applique à **sp_control_plan_guide** quand DROP ou DROP ALL est spécifié.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_PROCEDURE
    :::column-end:::
    :::column:::
        ALTER_PROCEDURE (S’applique à l’instruction ALTER PROCEDURE et à **sp_procoption**.)
    :::column-end:::
    :::column:::
        DROP_PROCEDURE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_QUEUE
    :::column-end:::
    :::column:::
        ALTER_QUEUE
    :::column-end:::
    :::column:::
        DROP_QUEUE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_REMOTE_SERVICE_BINDING
    :::column-end:::
    :::column:::
        ALTER_REMOTE_SERVICE_BINDING
    :::column-end:::
    :::column:::
        DROP_REMOTE_SERVICE_BINDING
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SPATIAL_INDEX
    :::column-end:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        RENAME (S’applique à **sp_rename**)
    :::column-end:::
    :::column:::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ROLE (S’applique à l’instruction CREATE ROLE, à **sp_addrole**et à **sp_addgroup**.)
    :::column-end:::
    :::column:::
        ALTER_ROLE
    :::column-end:::
    :::column:::
        DROP_ROLE (S’applique à l’instruction DROP ROLE, à **sp_droprole**et à **sp_dropgroup**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_ROLE_MEMBER
    :::column-end:::
    :::column:::
        DROP_ROLE_MEMBER
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ROUTE
    :::column-end:::
    :::column:::
        ALTER_ROUTE
    :::column-end:::
    :::column:::
        DROP_ROUTE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_RULE
    :::column-end:::
    :::column:::
        DROP_RULE
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        BIND_RULE (S’applique à **sp_bindrule**.)
    :::column-end:::
    :::column:::
        UNBIND_RULE (S’applique à **sp_unbindrule**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SCHEMA (S’applique à l’instruction CREATE SCHEMA, à **sp_addrole**, à **sp_adduser**, à **sp_addgroup**et à **sp_grantdbaccess**.)
    :::column-end:::
    :::column:::
        ALTER_SCHEMA (S’applique à l’instruction ALTER SCHEMA et à **sp_changeobjectowner**.)
    :::column-end:::
    :::column:::
        DROP_SCHEMA
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SEARCH_PROPERTY_LIST
    :::column-end:::
    :::column:::
        ALTER_SEARCH_PROPERTY_LIST
    :::column-end:::
    :::column:::
        DROP_SEARCH_PROPERTY_LIST
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
    :::column:::
        CREATE_SEQUENCE_EVENTS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_ROLE
    :::column-end:::
    :::column:::
        ALTER_SERVER_ROLE
    :::column-end:::
    :::column:::
        DROP_SERVER_ROLE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVICE
    :::column-end:::
    :::column:::
        ALTER_SERVICE
    :::column-end:::
    :::column:::
        DROP_SERVICE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ALTER_SERVICE_MASTER_KEY
    :::column-end:::
    :::column:::
        BACKUP_SERVICE_MASTER_KEY
    :::column-end:::
    :::column:::
        RESTORE_SERVICE_MASTER_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SIGNATURE (pour les opérations de signature sur les objets non compris dans l'étendue du schéma ; base de données, assembly, déclencheur)
    :::column-end:::
    :::column:::
        DROP_SIGNATURE
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SIGNATURE_SCHEMA_OBJECT (pour les objets compris dans l'étendue du schéma ; procédures stockées, fonctions)
    :::column-end:::
    :::column:::
        DROP_SIGNATURE_SCHEMA_OBJECT
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SPATIAL_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX peut être utilisé pour les index spatiaux.
    :::column-end:::
    :::column:::
        DROP_INDEX peut être utilisé pour les index spatiaux.
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_STATISTICS
    :::column-end:::
    :::column:::
        DROP_STATISTICS
    :::column-end:::
    :::column:::
        UPDATE_STATISTICS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SYMMETRIC_KEY
    :::column-end:::
    :::column:::
        ALTER_SYMMETRIC_KEY
    :::column-end:::
    :::column:::
        DROP_SYMMETRIC_KEY
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SYNONYM
    :::column-end:::
    :::column:::
        DROP_SYNONYM
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TABLE
    :::column-end:::
    :::column:::
        ALTER_TABLE (S’applique à l’instruction ALTER TABLE et à **sp_tableoption**.)
    :::column-end:::
    :::column:::
        DROP_TABLE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TRIGGER
    :::column-end:::
    :::column:::
        ALTER_TRIGGER (S’applique à l’instruction ALTER TRIGGER et à **sp_settriggerorder**.)
    :::column-end:::
    :::column:::
        DROP_TRIGGER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_TYPE (S’applique à l’instruction CREATE TYPE et à **sp_addtype**.)
    :::column-end:::
    :::column:::
        DROP_TYPE (S’applique à l’instruction DROP TYPE et à **sp_droptype**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_USER (S’applique à l’instruction CREATE USER, à **sp_adduser**et à **sp_grantdbaccess**.)
    :::column-end:::
    :::column:::
        ALTER_USER (S’applique à l’instruction ALTER USER et à **sp_change_users_login**.)
    :::column-end:::
    :::column:::
        DROP_USER (S’applique à l’instruction DROP USER, à **sp_dropuser**et à **sp_revokedbaccess**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_VIEW
    :::column-end:::
    :::column:::
        ALTER_VIEW
    :::column-end:::
    :::column:::
        DROP_VIEW
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_XML_INDEX
    :::column-end:::
    :::column:::
        ALTER_INDEX peut être utilisé pour les index XML.
    :::column-end:::
    :::column:::
        DROP_INDEX peut être utilisé pour les index XML.
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_XML_SCHEMA_COLLECTION
    :::column-end:::
    :::column:::
        ALTER_XML_SCHEMA_COLLECTION
    :::column-end:::
    :::column:::
        DROP_XML_SCHEMA_COLLECTION
    :::column-end:::
:::row-end:::
 
## <a name="ddl-statements-that-have-server-scope"></a>Instructions DDL qui ont une étendue à l'échelle du serveur  
 Les déclencheurs ou les notifications d'événements DDL peuvent être créés de façon à se déclencher en réponse aux événements suivants lorsqu'ils se produisent à un emplacement quelconque dans l'instance du serveur.  
  
:::row:::
    :::column:::
        ALTER_AUTHORIZATION_SERVER
    :::column-end:::
    :::column:::
        ALTER_SERVER_CONFIGURATION
    :::column-end:::
    :::column:::
        ALTER_INSTANCE (S’applique à **sp_configure** et à **sp_addserver** quand une instance du serveur local est spécifiée.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_AVAILABILITY_GROUP
    :::column-end:::
    :::column:::
        ALTER_AVAILABILITY_GROUP
    :::column-end:::
    :::column:::
        DROP_AVAILABILITY_GROUP
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CREDENTIAL
    :::column-end:::
    :::column:::
        ALTER_CREDENTIAL
    :::column-end:::
    :::column:::
        DROP_CREDENTIAL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
    :::column:::
        ALTER_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
    :::column:::
        DROP_CRYPTOGRAPHIC_PROVIDER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_DATABASE
    :::column-end:::
    :::column:::
        ALTER_DATABASE (S’applique à l’instruction ALTER DATABASE et à **sp_fulltext_database**.)
    :::column-end:::
    :::column:::
        DROP_DATABASE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_ENDPOINT
    :::column-end:::
    :::column:::
        ALTER_ENDPOINT
    :::column-end:::
    :::column:::
        DROP_ENDPOINT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EVENT_SESSION
    :::column-end:::
    :::column:::
        ALTER_EVENT_SESSION
    :::column-end:::
    :::column:::
        DROP_EVENT_SESSION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_EXTENDED_PROCEDURE (S’applique à **sp_addextendedproc**.)
    :::column-end:::
    :::column:::
        DROP_EXTENDED_PROCEDURE (S’applique à **sp_dropextendedproc**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LINKED_SERVER (S’applique à **sp_addlinkedserver**.)
    :::column-end:::
    :::column:::
        ALTER_LINKED_SERVER (S’applique à **sp_serveroption**.)
    :::column-end:::
    :::column:::
        DROP_LINKED_SERVER (S’applique à **sp_dropserver** quand un serveur lié est spécifié.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LINKED_SERVER_LOGIN (S’applique à **sp_addlinkedsrvlogin**.)
    :::column-end:::
    :::column:::
        DROP_LINKED_SERVER_LOGIN (S’applique à **sp_droplinkedsrvlogin**.)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_LOGIN (S’applique à l’instruction CREATE LOGIN, à **sp_addlogin**, à **sp_grantlogin**, à **xp_grantlogin**et à **sp_denylogin** en cas d’utilisation sur une connexion inexistante qui doit être créée de manière implicite.)
    :::column-end:::
    :::column:::
        ALTER_LOGIN (S’applique à l’instruction ALTER LOGIN, à **sp_defaultdb**, à **sp_defaultlanguage**, à **sp_password**et à **sp_change_users_login** quand *Auto_Fix* est spécifié.)
    :::column-end:::
    :::column:::
        DROP_LOGIN (S’applique à l’instruction DROP LOGIN, à **sp_droplogin**, à **sp_revokelogin**et à **xp_revokelogin**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_MESSAGE (S’applique à **sp_addmessage**.)
    :::column-end:::
    :::column:::
        ALTER_MESSAGE (S’applique à **sp_altermessage**.)
    :::column-end:::
    :::column:::
        DROP_MESSAGE (S’applique à **sp_dropmessage**.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_REMOTE_SERVER (S’applique à **sp_addserver**.)
    :::column-end:::
    :::column:::
        ALTER_REMOTE_SERVER (S’applique à **sp_setnetname**.)
    :::column-end:::
    :::column:::
        DROP_REMOTE_SERVER (S’applique à **sp_dropserver** quand un serveur distant est spécifié.)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_RESOURCE_POOL
    :::column-end:::
    :::column:::
        ALTER_RESOURCE_POOL
    :::column-end:::
    :::column:::
        DROP_RESOURCE_POOL
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        GRANT_SERVER
    :::column-end:::
    :::column:::
        DENY_SERVER
    :::column-end:::
    :::column:::
        REVOKE_SERVER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ADD_SERVER_ROLE_MEMBER
    :::column-end:::
    :::column:::
        DROP_SERVER_ROLE_MEMBER
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_AUDIT
    :::column-end:::
    :::column:::
        ALTER_SERVER_AUDIT
    :::column-end:::
    :::column:::
        DROP_SERVER_AUDIT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
    :::column:::
        ALTER_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
    :::column:::
        DROP_SERVER_AUDIT_SPECIFICATION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CREATE_WORKLOAD_GROUP
    :::column-end:::
    :::column:::
        ALTER_WORKLOAD_GROUP
    :::column-end:::
    :::column:::
        DROP_WORKLOAD_GROUP
    :::column-end:::
:::row-end:::
 
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [Notifications d'événements](../../relational-databases/service-broker/event-notifications.md)   
 [Groupes d’événements DDL](../../relational-databases/triggers/ddl-event-groups.md)  
  
  
