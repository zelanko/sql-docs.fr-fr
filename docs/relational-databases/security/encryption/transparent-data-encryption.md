---
title: Chiffrement TDE (Transparent Data Encryption) | Microsoft Docs
description: Découvrez Transparent Data Encryption, qui chiffre les bases de données SQL Server, Azure SQL Database et Azure Synapse Analytics. Il est également appelé chiffrement des données au repos.
ms.custom: ''
ms.date: 05/09/2019
ms.prod: sql
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption
- database encryption key, about
- TDE
- database encryption key
- TDE, about
- Transparent Data Encryption, about
- encryption [SQL Server], transparent data encryption
ms.assetid: c75d0d4b-4008-4e71-9a9d-cee2a566bd3b
author: jaszymas
ms.author: jaszymas
ms.reviewer: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b37932efe96f0892e5e2e3ce6c30c4adf1de557d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86002791"
---
# <a name="transparent-data-encryption-tde"></a>Transparent Data Encryption (TDE)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

*Transparent Data Encryption* (TDE) chiffre les fichiers de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] et [!INCLUDE[ssSDWfull](../../../includes/sssdwfull-md.md)]. Ce chiffrement est connu sous le nom de chiffrement de données au repos.

Pour sécuriser une base de données, vous pouvez prendre certaines précautions, à savoir :

* Concevoir un système sécurisé.
* Chiffrer les ressources confidentielles.
* Créer un pare-feu autour des serveurs de base de données.

Or, un tiers malveillant qui subtiliserait des médias physiques comme des disques durs ou des bandes de sauvegarde pourrait restaurer ou attacher la base de données et parcourir les données qu’elle contient.

Il existe une solution qui consiste à chiffrer les données sensibles dans une base de données et à utiliser un certificat pour protéger les clés qui chiffrent les données. Cette solution empêche quiconque ne disposant pas des clés d’utiliser les données. Vous devez cependant planifier ce type de protection à l’avance.

TDE assure un chiffrement et un déchiffrement des données et des fichiers journaux en E/S et en temps réel. Le chiffrement utilise une clé de chiffrement de base de données. L’enregistrement de démarrage de la base de données stocke la clé pour la mettre à disposition pendant la récupération. La clé de chiffrement de base de données est une clé symétrique. Elle est sécurisée par un certificat stocké dans la base de données MASTER du serveur ou par une clé asymétrique protégée par un module EKM.

TDE protège les données au repos, c’est-à-dire les fichiers de données et les fichiers journaux. Il vous permet d’être en conformité avec de nombreuses lois, réglementations et directives établies dans différents secteurs d’activité. Cette possibilité permet aux développeurs de logiciels de chiffrer les données à l’aide des algorithmes de chiffrement AES et 3DES sans modifier les applications existantes.

> [!IMPORTANT]
> TDE n’assure pas de chiffrement sur les canaux de communication. Pour plus d’informations sur le chiffrement des données sur les canaux de communication, consultez [Activer les connexions chiffrées dans le moteur de base de données (Gestionnaire de configuration SQL Server)](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).
>
>**Rubriques connexes :**
>
> - [Transparent Data Encryption avec Azure SQL Database](../../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md)
> - [Prise en main du chiffrement transparent des données (TDE) sur SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-encryption-tde-tsql/)
> - [Déplacer une base de données protégée par le chiffrement transparent des données vers un autre serveur SQL Server](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md)
> - [Activer le chiffrement transparent des données à l’aide de la gestion de clés extensible (EKM)](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)
> - [Utiliser le connecteur SQL Server avec les fonctionnalités de chiffrement SQL](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md)
> - [Blog sur la sécurité SQL Server : chiffrement transparent des données (avec FAQ)](https://blogs.msdn.microsoft.com/sqlsecurity/2016/10/05/feature-spotlight-transparent-data-encryption-tde/)

## <a name="about-tde"></a>À propos du chiffrement transparent des données

Le chiffrement d’un fichier de base de données s’effectue au niveau de la page. Les pages au sein d’une base de données chiffrée sont chiffrées avant d’être écrites sur disque et déchiffrées au moment d’être lues en mémoire. TDE n’augmente pas la taille de la base de données chiffrée.

### <a name="information-applicable-to-sssds"></a>Informations applicables à [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]

Quand vous utilisez TDE avec [!INCLUDE[sqldbesa](../../../includes/sqldbesa-md.md)] V12, [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] crée automatiquement le certificat de niveau serveur stocké dans la base de données MASTER. Pour déplacer une base de données TDE sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], vous n’avez pas besoin de déchiffrer la base de données pour l’opération de déplacement. Pour plus d’informations sur l’utilisation de TDE avec [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], consultez [Transparent Data Encryption avec Azure SQL Database](../../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md).

### <a name="information-applicable-to-ssnoversion"></a>Informations applicables à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]

Après avoir sécurisé une base de données, vous pouvez la restaurer à l’aide du certificat adéquat. Pour plus d'informations sur les certificats, consultez [SQL Server Certificates and Asymmetric Keys](../../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).

Après avoir activé TDE, sauvegardez immédiatement le certificat et la clé privée associée. Si le certificat devient indisponible ou si vous restaurez ou attachez la base de données sur un autre serveur, vous aurez besoin d’une sauvegarde du certificat et de la clé privée. À défaut, vous ne pourrez pas ouvrir la base de données.

Conservez le certificat de chiffrement même si vous désactivez TDE sur la base de données. Même si la base de données n’est pas chiffrée, des parties du journal des transactions peuvent rester protégées. Le certificat peut aussi vous être utile pour certaines opérations tant que vous n’effectuez pas une sauvegarde complète de la base de données.

Vous pouvez toujours utiliser un certificat dont la date d’expiration est passée pour chiffrer et déchiffrer des données avec TDE.

### <a name="encryption-hierarchy"></a>Hiérarchie de chiffrement

L'illustration ci-dessous montre l'architecture du chiffrement TDE. Seuls les éléments de niveau base de données (la clé de chiffrement de base de données et les parties ALTER DATABASE) sont configurables par l’utilisateur quand vous utilisez TDE sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)].

![Architecture de Transparent Data Encryption](../../../relational-databases/security/encryption/media/tde-architecture.png)

## <a name="using-transparent-data-encryption"></a>Utilisation du chiffrement transparent des données

Pour utiliser le chiffrement transparent des données, procédez comme suit :

**S'applique à**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

1. Créez une clé principale.

1. Créez ou procurez-vous un certificat protégé par la clé principale.

1. Créez une clé de chiffrement de base de données et protégez-la à l’aide du certificat.

1. Configurez la base de données pour qu’elle utilise le chiffrement.

L’exemple ci-dessous illustre le chiffrement et le déchiffrement de la base de données `AdventureWorks2012` à l’aide d’un certificat nommé `MyServerCert` sur le serveur.

```sql
USE master;
GO
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';
go
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';
go
USE AdventureWorks2012;
GO
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_128
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;
GO
ALTER DATABASE AdventureWorks2012
SET ENCRYPTION ON;
GO
```

Les opérations de chiffrement et de déchiffrement sont planifiées sur des threads d'arrière-plan par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour consulter l’état de ces opérations, utilisez les vues catalogue et les vues de gestion dynamique décrits dans le tableau plus loin dans cet article.

> [!CAUTION]
> Les fichiers de sauvegarde de base de données pour lesquelles TDE est activé sont aussi chiffrés avec la clé de chiffrement de base de données. Ainsi, quand vous restaurez ces sauvegardes, le certificat qui protège la clé de chiffrement de base de données doit être disponible. Par conséquent, au-delà de la sauvegarder de la base de données, pensez à conserver les sauvegardes des certificats de serveur. Si les certificats ne sont plus disponibles, vous perdrez des données.
>
> Pour plus d'informations, consultez [SQL Server Certificates and Asymmetric Keys](../../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).

## <a name="commands-and-functions"></a>Commandes et fonctions

Pour que les instructions suivantes acceptent les certificats TDE, utilisez une clé principale de base de données pour les chiffrer. Si vous les chiffrez par mot de passe uniquement, les instructions les rejettent en tant que chiffreurs.

> [!IMPORTANT]
> Si vous protégez les certificats par mot de passe après avoir été utilisés par TDE, la base de données devient inaccessible après un redémarrage.

Le tableau suivant fournit des liens et des explications pour les commandes et les fonctions TDE :

|Commande ou fonction|Objectif|
|-------------------------|-------------|
|[CREATE DATABASE ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-database-encryption-key-transact-sql.md)|Crée une clé qui chiffre une base de données| 
|[ALTER DATABASE ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-database-encryption-key-transact-sql.md)|Change la clé qui chiffre une base de données|
|[DROP DATABASE ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/drop-database-encryption-key-transact-sql.md)|Supprime la clé qui chiffre une base de données|
|[Options SET d’ALTER DATABASE (Transact-SQL)](../../../t-sql/statements/alter-database-transact-sql-set-options.md)|Présente l’option **ALTER DATABASE** qui est utilisée pour activer TDE|

## <a name="catalog-views-and-dynamic-management-views"></a>Vues catalogue et vues de gestion dynamique

 Le tableau suivant indique les affichages catalogue et les vues de gestion dynamique du chiffrement transparent des données.

|Affichage catalogue ou vue de gestion dynamique|Objectif|
|---------------------------------------------|-------------|
|[sys.databases (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|Vue catalogue qui affiche des informations sur la base de données|
|[sys.certificates (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|Vue catalogue qui présente les certificats d’une base de données|
|[sys.dm_database_encryption_keys (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md)|Vue de gestion dynamique qui fournit des informations sur les clés de chiffrement d’une base de données et sur l’état de chiffrement|

## <a name="permissions"></a>Autorisations

Chaque fonctionnalité et commande TDE nécessite des autorisations individuelles, décrites dans les tableaux précédents.

La consultation des métadonnées impliquées avec TDE nécessite l’autorisation VIEW DEFINITION sur un certificat.

## <a name="considerations"></a>Considérations

Lorsqu'une analyse de rechiffrement est en cours pour une opération de chiffrement de la base de données, les opérations de maintenance sur la base de données sont désactivées. Vous pouvez utiliser le paramètre du mode mono-utilisateur pour la base de données pour effectuer des opérations de maintenance. Pour plus d’informations, consultez [Définir une base de données en mode mono-utilisateur](../../../relational-databases/databases/set-a-database-to-single-user-mode.md).

Utilisez la vue de gestion dynamique sys.dm_database_encryption_keys pour déterminer l’état de chiffrement de la base de données. Pour plus d’informations, consultez la section « Vues catalogue et vues de gestion dynamique » plus haut dans cet article.

Avec TDE, tous les fichiers et groupes de fichiers d’une base de données sont chiffrés. Si la base de données contient un groupe de fichiers marqué READ ONLY, l’opération de chiffrement de la base de données échoue.

Si vous utilisez une base de données dans la mise en miroir de bases de données ou la copie des journaux de transaction, les deux bases de données sont chiffrées. Les transactions de journal sont chiffrées quand elles passent de l’une à l’autre.

> [!IMPORTANT]
> Les index de recherche en texte intégral sont chiffrés dès lors qu’une base de données est définie pour le chiffrement. Les index de ce type qui ont été créés dans une version de SQL Server antérieure à SQL Server 2008 sont importés dans la base de données par SQL Server 2008 ou version ultérieure et sont chiffrés par TDE.

> [!TIP]
> Pour superviser les changements d’état TDE d’une base de données, utilisez SQL Server Audit ou l’audit SQL Database. Pour SQL Server, TDE est suivi par le groupe d’actions d’audit DATABASE_CHANGE_GROUP, que vous trouverez dans [Actions et groupes d’actions SQL Server Audit ](../../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).

### <a name="restrictions"></a>Restrictions

Les opérations suivantes ne sont pas autorisées pendant le chiffrement initial de la base de données, un changement de clé ou le chiffrement de la base de données :

- Suppression d’un fichier dans un groupe de fichiers de base de données

- Suppression d’une base de données

- Mise hors connexion d’une base de données

- Détachement d'une base de données

- Passage d'une base de données ou d'un groupe de fichiers à l'état READ ONLY

Les opérations suivantes ne sont pas autorisées pendant l’exécution des instructions CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY et ALTER DATABASE...SET ENCRYPTION :

- Suppression d’un fichier dans un groupe de fichiers de base de données

- Suppression d’une base de données

- Mise hors connexion d’une base de données

- Détachement d'une base de données

- Passage d'une base de données ou d'un groupe de fichiers à l'état READ ONLY

- Utilisation d’une commande ALTER DATABASE

- Démarrage d’une sauvegarde de base de données ou de fichiers de base de données

- Démarrage d’une restauration de base de données ou de fichiers de base de données

- Création d’un instantané

Les opérations ou conditions suivantes empêchent l’exécution des instructions CREATE DATABASE ENCRYPTION KEY, ALTER DATABASE ENCRYPTION KEY, DROP DATABASE ENCRYPTION KEY et ALTER DATABASE...SET ENCRYPTION :

- Une base de données est en lecture seule ou comporte des groupes de fichiers en lecture seule.

- Une commande ALTER DATABASE est en cours d’exécution.

- Une sauvegarde de données est en cours d’exécution.

- Une base de données est à l’état hors connexion ou en cours de restauration.

- Un instantané est en cours.

- Des tâches de maintenance de base de données sont en cours d’exécution.

Pendant la création de fichiers de base de données, l’initialisation instantanée des fichiers n’est pas disponible quand TDE est activé.

Pour chiffrer une clé de chiffrement de base de données avec une clé asymétrique, celle-ci doit être mise à la disposition d’un fournisseur de gestion de clés extensible.

### <a name="transparent-data-encryption-and-transaction-logs"></a>Transparent Data Encryption et journaux de transactions

Le fait qu’une base de données utilise TDE entraîne la suppression de la partie restante du journal des transactions virtuel actuel. Cette suppression impose la création du journal des transactions suivant. Ce comportement est la garantie qu’aucun texte en clair n’est conservé dans les journaux après que la base de données est définie pour le chiffrement.

Pour déterminer l’état du chiffrement des fichiers journaux, consultez la colonne `encryption_state` dans la vue `sys.dm_database_encryption_keys`, comme dans l’exemple suivant :

```sql
USE AdventureWorks2012;
GO
/* The value 3 represents an encrypted state
   on the database and transaction logs. */
SELECT *
FROM sys.dm_database_encryption_keys
WHERE encryption_state = 3;
GO
```

Pour plus d’informations sur l’architecture des fichiers journaux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [Journal des transactions (SQL Server)](../../../relational-databases/logs/the-transaction-log-sql-server.md).

Avant de changer de clé de chiffrement de base de données, la clé de chiffrement de base de données précédente chiffre toutes les données écrites dans le journal des transactions.

Si vous changez de clé de chiffrement de base de données à deux reprises, vous devez sauvegarder le journal avant de pouvoir changer à nouveau la clé de chiffrement de base de données.

### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Transparent Data Encryption et base de données système tempdb

La base de données système **tempdb** est chiffrée si une autre base de données de l’instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est chiffrée à l’aide de TDE. Ce chiffrement peut avoir des conséquences sur le niveau de performance des bases de données non chiffrées sur la même instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la base de données système **tempdb**, consultez [Base de données tempdb](../../../relational-databases/databases/tempdb-database.md).

### <a name="transparent-data-encryption-and-replication"></a>Transparent Data Encryption et réplication

La réplication ne réplique pas automatiquement sous une forme chiffrée les données d’une base de données pour laquelle TDE est activé. Si vous voulez protéger les bases de données de distribution et d’abonné, activez TDE séparément.

La réplication d’instantané peut stocker les données dans des fichiers intermédiaires non chiffrés comme les fichiers BCP. La distribution initiale des données pour la réplication transactionnelle et de fusion le peut également. Au cours d’une réplication de ce type, vous pouvez activer le chiffrement pour protéger le canal de communication.

Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données (Gestionnaire de configuration SQL Server)](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).

### <a name="transparent-data-encryption-and-filestream-data"></a>Transparent Data Encryption et données FILESTREAM

Les données **FILESTREAM** ne sont pas chiffrées même quand vous activez TDE.

<a name="scan-suspend-resume"></a>

## <a name="transparent-data-encryption-scan"></a>Analyse Transparent Data Encryption

Pour activer TDE sur une base de données, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit effectuer une analyse de chiffrement. L’analyse lit chaque page des fichiers de données dans le pool de mémoires tampons, puis réécrit les pages chiffrées sur disque.

Pour vous permettre de mieux contrôler l’analyse du chiffrement, [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] intègre l’analyse TDE, qui propose une syntaxe de suspension (« suspend ») et de reprise (« resume »). Vous pouvez ainsi suspendre l’analyse quand le système est soumis à une charge de travail intense ou pendant les heures de pointe et reprendre l’analyse à un moment ultérieur.

Pour suspendre l’analyse du chiffrement TDE, utilisez la syntaxe suivante :

```sql
ALTER DATABASE <db_name> SET ENCRYPTION SUSPEND;
```

De la même manière, utilisez la syntaxe suivante pour reprendre l’analyse du chiffrement TDE :

```sql
ALTER DATABASE <db_name> SET ENCRYPTION RESUME;
```

La colonne encryption_scan_state a été ajoutée à la vue de gestion dynamique sys.dm_database_encryption_keys. Elle indique l’état actuel de l’analyse du chiffrement. Il existe également une nouvelle colonne appelée encryption_scan_modify_date qui contient la date et l’heure du dernier changement d’état de l’analyse du chiffrement.

Si l’instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] redémarre alors que l’analyse du chiffrement y est suspendue, un message est consigné dans le journal des erreurs pendant le démarrage. Le message indique qu’une analyse existante a été suspendue.

## <a name="transparent-data-encryption-and-buffer-pool-extension"></a>Transparent Data Encryption et extension du pool de mémoires tampons

Quand vous chiffrez une base de données à l’aide de TDE, les fichiers associés à l’extension du pool de mémoires tampons (BPE) ne sont pas chiffrés. Pour ces fichiers, utilisez des outils de chiffrement comme BitLocker ou EFS au niveau du système de fichiers.

## <a name="transparent-data-encryption-and-in-memory-oltp"></a>Chiffrement transparent des données et OLTP en mémoire

Vous pouvez activer TDE sur une base de données contenant des objets OLTP en mémoire. Dans [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)], les enregistrements de journal et les données OLTP en mémoire sont chiffrés si vous activez TDE. Dans [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], les enregistrements de journal OLTP en mémoire sont chiffrés si vous activez TDE, mais les fichiers contenus dans le groupe de fichiers MEMORY_OPTIMIZED_DATA ne le sont pas.

## <a name="related-tasks"></a>Tâches associées

[Déplacer une base de données protégée par le chiffrement transparent des données vers un autre serveur SQL Server](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md)  
[Activer le chiffrement transparent des données à l’aide de la gestion de clés extensible (EKM)](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
[Gestion de clés extensible à l’aide d’Azure Key Vault (SQL Server)](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  

## <a name="related-content"></a>Contenu connexe

[Transparent Data Encryption avec Azure SQL Database](../../../relational-databases/security/encryption/transparent-data-encryption-azure-sql.md)  
[Prise en main du chiffrement transparent des données (TDE) sur SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-encryption-tde-tsql/)  
[Chiffrement SQL Server](../../../relational-databases/security/encryption/sql-server-encryption.md)  
[SQL Server et clés de chiffrement de base de données (moteur de base de données)](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

## <a name="see-also"></a>Voir aussi

[Centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database](../../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
[FILESTREAM (SQL Server)](../../../relational-databases/blob/filestream-sql-server.md)  
