---
title: Chiffrement transparent des données - Parallel Data Warehouse | Microsoft Docs
description: Chiffrement transparent des données (TDE) pour Parallel Data Warehouse (PDW) effectue le chiffrement d’e/s en temps réel et le déchiffrement des données et fichiers journaux des transactions et les fichiers de journaux PDW spéciales. »
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f30d22725e7d0fd099cf2976af42d74d08a93b22
ms.sourcegitcommit: 2e038db99abef013673ea6b3535b5d9d1285c5ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39400612"
---
# <a name="transparent-data-encryption"></a>chiffrement transparent des données
Vous pouvez prendre plusieurs précautions pour mieux sécuriser la base de données comme par exemple concevoir un système sécurisé, chiffrer les ressources confidentielles et créer un pare-feu autour des serveurs de base de données. Toutefois, pour un scénario dans lequel le support physique (par exemple, les lecteurs ou les bandes de sauvegarde) est volé, une personne malveillante peut juste restaurer ou attacher la base de données et parcourir les données. Une solution consiste à chiffrer les données sensibles dans la base de données et à protéger les clés utilisées pour chiffrer les données avec un certificat. Cela empêche toute personne qui ne dispose pas des clés d'utiliser les données, mais ce type de protection doit être planifié à l'avance.  
  
*Chiffrement transparent des données* (TDE) effectue le chiffrement d’e/s en temps réel et le déchiffrement des données et les fichiers journaux des transactions et le PDW spécial des fichiers journaux. Le chiffrement utilise une clé de chiffrement de base de données (DEK), stockée dans l'enregistrement de démarrage de base de données pour être disponible pendant la récupération. La clé DEK est une clé symétrique sécurisée à l’aide d’un certificat stocké dans la base de données master de l’ordinateur SQL Server PDW. Le chiffrement transparent des données protège les données « au repos », autrement dit les fichiers de données et les fichiers journaux. Il permet de se conformer à de nombreuses lois, règles et instructions établies dans différents secteurs professionnels. Cette fonctionnalité permet aux développeurs de logiciels de chiffrer les données à l’aide d’algorithmes de chiffrement AES et 3DES sans modifier les applications existantes.  
  
> [!IMPORTANT]  
> Chiffrement transparent des données ne fournissent pas de chiffrement pour les données circulant entre le client et le PDW. Pour plus d’informations sur le chiffrement des données entre le client et SQL Server PDW, consultez [configurer un certificat](provision-certificate.md).  
>   
> Chiffrement transparent des données ne chiffrement pas les données en déplacement ou en cours d’utilisation. Le trafic interne entre les composants PDW à l’intérieur de l’ordinateur SQL Server PDW n’est pas chiffré. Données temporairement stockées dans les mémoires tampons ne sont pas chiffrées. Pour atténuer ce risque, contrôler l’accès physique et connexions à l’ordinateur SQL Server PDW.  
  
Une fois sécurisée, la base de données peut être restaurée à l'aide du certificat approprié.  
  
> [!NOTE]  
> Lorsque vous créez un certificat pour le chiffrement transparent des données, vous devez immédiatement sauvegarder il, ainsi que la clé privée associée. Dans l'éventualité où le certificat ne serait plus disponible ou que vous deviez restaurer ou attacher la base de données sur un autre serveur, vous devez disposer de sauvegardes du certificat et de la clé privée, sans quoi vous ne pourrez pas ouvrir la base de données. Le certificat de chiffrement doit être conservé même si le chiffrement transparent des données n'est plus activé sur la base de données. Même si la base de données n'est pas chiffrée, des parties du journal des transactions peuvent toujours être protégées, et le certificat peut être nécessaire pour certaines opérations tant que la sauvegarde complète de la base de données n'a pas été effectuée. Un certificat qui a dépassé sa date d'expiration peut toujours être utilisé pour chiffrer et déchiffrer les données avec le chiffrement transparent des données.  
  
Le chiffrement du fichier de base de données est effectué au niveau de la page. Les pages d'une base de données chiffrée sont chiffrées avant d'être écrites sur le disque et déchiffrées lorsqu'elles sont lues en mémoire. Le chiffrement transparent des données n'augmente pas la taille de la base de données chiffrée.  
  
L’illustration suivante montre la hiérarchie des clés de chiffrement transparent des données :  
  
![Affiche la hiérarchie](media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-tde"></a>À l’aide du chiffrement Transparent des données  
Pour utiliser le chiffrement transparent des données, procédez comme suit : Les trois premières étapes sont uniquement effectuées une seule fois, lors de la préparation de SQL Server PDW pour prendre en charge le chiffrement transparent des données.  
  
1.  Créer une clé principale dans la base de données master.  
  
2.  Utilisez **sp_pdw_database_encryption pour** pour activer le chiffrement transparent des données sur le serveur SQL Server PDW. Cette opération modifie les bases de données temporaires afin de garantir la protection des données temporaires futures et will fail if tentées lorsqu’il existe des sessions actives qui ont des tables temporaires. **sp_pdw_database_encryption pour** active sur le masquage des données utilisateur dans les journaux du système PDW. (Pour plus d’informations sur le masquage des données utilisateur dans les journaux du système PDW, consultez [sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md).)  
  
3.  Utilisez [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) pour créer des informations d’identification qui peuvent authentifier et écrire sur le partage où la sauvegarde du certificat sera stockée. Si une information d’identification existe déjà pour le serveur de stockage souhaité, vous pouvez utiliser les informations d’identification existantes.  
  
4.  Dans la base de données master, créez un certificat protégé par la clé principale.  
  
5.  Sauvegardez le certificat pour le partage de stockage.  
  
6.  Dans la base de données utilisateur, créez une clé de chiffrement de base de données et le protéger par le certificat est stocké dans la base de données master.  
  
7.  Utilisez la `ALTER DATABASE` instruction pour chiffrer la base de données à l’aide du chiffrement transparent des données.  
  
L’exemple suivant illustre le chiffrement de la `AdventureWorksPDW2012` de base de données à l’aide d’un certificat nommé `MyServerCert`, créée dans SQL Server PDW.  
  
**Premier : Activer TDE sur SQL Server PDW.** Cette action est uniquement nécessaire qu’une seule fois.  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
-- Add a credential that can write to the share  
-- A credential created for a backup can be used if you wish  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
**Deuxième : Créer et sauvegarder un certificat dans la base de données master.** Cette action est uniquement obligatoire une fois. Vous pouvez avoir un certificat distinct pour chaque base de données (recommandé), ou vous pouvez protéger plusieurs bases de données avec un certificat.  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';  
GO  
  
-- Back up the certificate with private key  
BACKUP CERTIFICATE MyServerCert   
    TO FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'  
    WITH PRIVATE KEY   
    (   
        FILE = '\\SECURE_SERVER\cert\MyServerCert.key',  
        ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>'   
    )   
GO  
```  
  
**Dernière : Créer la clé DEK et utilisez ALTER DATABASE pour chiffrer une base de données utilisateur.** Cette action est répétée pour chaque base de données est protégée par chiffrement transparent des données.  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_128  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
  
ALTER DATABASE AdventureWorksPDW2012 SET ENCRYPTION ON;  
GO  
```  
  
Les opérations de chiffrement et de déchiffrement sont planifiées sur des threads d’arrière-plan par SQL Server. Vous pouvez afficher l’état de ces opérations en utilisant les affichages catalogue et les vues de gestion dynamique dans la liste qui apparaît plus loin dans cet article.  
  
> [!CAUTION]  
> Les fichiers de sauvegarde des bases de données pour lesquelles le chiffrement transparent des données est activé sont également chiffrés à l'aide de la clé de chiffrement de base de données. En conséquence, lorsque vous restaurez ces sauvegardes, le certificat qui protège la clé de chiffrement de base de données doit être disponible. Cela signifie qu'en plus de sauvegarder la base de données, vous devez vous assurer que vous conservez des sauvegardes des certificats du serveur pour empêcher toute perte de données. Une perte de données interviendra si le certificat n'est plus disponible.  
  
## <a name="commands-and-functions"></a>Commandes et fonctions  
Les certificats TDE doivent être chiffrés par la clé principale de base de données pour être acceptés par les instructions suivantes.  
  
Le tableau suivant fournit des liens et des explications pour les commandes et les fonctions TDE.  
  
|Commande ou fonction|Fonction|  
|-----------------------|-----------|  
|[CRÉER LA CLÉ DE CHIFFREMENT DE BASE DE DONNÉES](../t-sql/statements/create-database-encryption-key-transact-sql.md)|Crée une clé permettant de chiffrer une base de données.|  
|[MODIFIER LA CLÉ DE CHIFFREMENT DE BASE DE DONNÉES](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|Modifie la clé qui permet de chiffrer une base de données.|  
|[DROP DATABASE ENCRYPTION KEY](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|Supprime la clé qui était utilisée pour chiffrer une base de données.|  
|[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)|Présente l'option **ALTER DATABASE** qui est utilisée pour activer le chiffrement transparent des données.|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>Affichages catalogue et vues de gestion dynamique  
Le tableau suivant indique les affichages catalogue et les vues de gestion dynamique du chiffrement transparent des données.  
  
|Affichage catalogue ou vue de gestion dynamique|Fonction|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|Affichage catalogue qui affiche des informations sur la base de données.|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|Affichage catalogue qui indique les certificats inclus dans une base de données.|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|Vue de gestion dynamique qui fournit des informations pour chaque nœud, sur les clés de chiffrement utilisé dans une base de données et l’état de chiffrement d’une base de données.|  
  
## <a name="permissions"></a>Permissions  
Chaque fonctionnalité et commande TDE requiert des autorisations individuelles, décrites dans les tableaux précédents.  
  
L’affichage des métadonnées impliquées dans le chiffrement transparent des données nécessite la `CONTROL SERVER` autorisation.  
  
## <a name="considerations"></a>Observations  
Lorsqu'une analyse de rechiffrement est en cours pour une opération de chiffrement de la base de données, les opérations de maintenance sur la base de données sont désactivées.  
  
Vous pouvez déterminer l’état du chiffrement de base de données en utilisant le **sys.dm_pdw_nodes_database_encryption_keys** vue de gestion dynamique. Pour plus d’informations, consultez le *affichages catalogue et vues de gestion dynamique* section plus haut dans cet article.  
  
### <a name="restrictions"></a>Restrictions  
Les opérations suivantes ne sont pas autorisées pendant la `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, ou `ALTER DATABASE...SET ENCRYPTION` instructions.  
  
-   Suppression de la base de données  
  
-   À l’aide un `ALTER DATABASE` commande.  
  
-   Lance une sauvegarde de base de données.  
  
-   Démarrage d’une restauration de base de données.  
  
Les opérations ou les conditions suivantes empêchera le `CREATE DATABASE ENCRYPTION KEY`, `ALTER DATABASE ENCRYPTION KEY`, `DROP DATABASE ENCRYPTION KEY`, ou `ALTER DATABASE...SET ENCRYPTION` instructions.  
  
-   Un `ALTER DATABASE` commande s’exécute.  
  
-   Une sauvegarde de données est en cours d'exécution.  
  
Lors de la création de fichiers de base de données, l'initialisation instantanée des fichiers n'est pas disponible lorsque le chiffrement transparent des données est activé.  
  
### <a name="areas-not-protected-by-tde"></a>Zones non protégés par chiffrement transparent des données  
Chiffrement transparent des données ne protège pas les tables externes.  
  
Chiffrement transparent des données ne protège pas les sessions de diagnostic. Les utilisateurs doivent être prudents pas aux requêtes avec paramètres sensibles, tandis que les sessions de diagnostic sont en cours d’utilisation. Sessions de diagnostic qui révèlent des informations sensibles doivent être supprimées dès qu’ils ne sont plus nécessaires.  
  
Les données protégées par chiffrement transparent des données sont déchiffrées lorsqu’elle est placée dans la mémoire de SQL Server PDW. Vidages de mémoire sont créés lorsque certains problèmes se produisent sur l’appliance. Vider les fichiers représentent le contenu de la mémoire au moment de l’apparence du problème et peut contenir des données sensibles dans une forme non chiffrée. Le contenu de vidages de mémoire doit-elle être examiné avant que celles-ci sont partagées avec d’autres.  
  
La base de données master n’est pas protégé par chiffrement transparent des données. Bien que la base de données master ne contient pas de données utilisateur, il ne contient des informations telles que des noms de connexion.  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Chiffrement transparent des données et journaux de transactions  
L’activation d’une base de données à utiliser le chiffrement transparent des données a pour effet de réinitialisation de la partie restante du journal des transactions virtuel pour forcer le journal des transactions virtuel suivant. Cela garantit qu'aucun texte en clair n'est conservé dans les journaux des transactions après que la base de données a été définie pour le chiffrement. Vous pouvez rechercher l’état du chiffrement de fichier journal sur chaque nœud PDW en consultant le `encryption_state` colonne dans la `sys.dm_pdw_nodes_database_encryption_keys` vue, comme dans cet exemple :  
  
```sql  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
           ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
Toutes les données écrites dans le journal des transactions avant une modification de la clé de chiffrement de base de données seront chiffrées à l'aide de la clé de chiffrement de base de données précédente.  
  
### <a name="pdw-activity-logs"></a>Journaux d’activité PDW  
SQL Server PDW gère un ensemble de journaux destinés à la résolution des problèmes. (Notez, ce n’est pas le journal des transactions, le journal des erreurs SQL Server ou le journal des événements Windows.) Ces journaux d’activité PDW peut contenir des instructions complètes en texte clair, certains d'entre eux peuvent contenir des données utilisateur. Sont des exemples typiques **insérer** et **mise à jour** instructions. Masquage des données utilisateur permettre être explicitement activé ou désactivée à l’aide de **sp_pdw_log_user_data_masking**. Activation du chiffrement sur SQL Server PDW automatiquement pour activer le masquage des données utilisateur dans les journaux d’activité PDW pour les protéger. **sp_pdw_log_user_data_masking** peut également servir pour masquer les instructions lorsque vous N'utilisez pas de chiffrement transparent des données, mais qui n’est pas recommandée, car elle réduit considérablement la capacité de l’équipe de Support Microsoft pour analyser les problèmes.  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Chiffrement transparent des données et base de données système tempdb  
La base de données système tempdb est chiffrée lorsque le chiffrement est activé à l’aide de [sp_pdw_database_encryption pour](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md). Cela est nécessaire avant que toute base de données puisse utiliser le chiffrement transparent des données. Cela peut avoir un effet de performances pour les bases de données non chiffrées sur la même instance de SQL Server PDW.  
  
## <a name="key-management"></a>Gestion de clés  
La clé de chiffrement de base de données (DEK) est protégée par les certificats stockés dans la base de données master. Ces certificats sont protégés par la clé principale de base de données (DMK) de la base de données master. La clé DMK doit être protégé par la clé principale du service (SMK) pour pouvoir être utilisé pour le chiffrement transparent des données.  
  
Le système peut accéder aux clés sans intervention humaine (par exemple, en fournissant un mot de passe). Si le certificat n’est pas disponible, le système génère un message d’erreur expliquant que la clé DEK ne peut pas être déchiffrée jusqu'à ce que le certificat approprié est disponible.  
  
Lorsque vous déplacez une base de données à partir d’une appliance vers une autre, le certificat utilisé pour protéger son « clé DEK doit d’abord être restaurée sur le serveur de destination. Puis la base de données peut être restaurée comme d’habitude. Pour plus d’informations, consultez la documentation de SQL Server standard, à l’adresse [déplacer une base de données protégé par chiffrement transparent des données vers un autre serveur SQL](http://technet.microsoft.com/library/ff773063.aspx).  
  
Certificats utilisés pour chiffrer le chiffrement doivent être conservées en tant qu’il existe des sauvegardes de base de données qui les utilisent. Sauvegardes de certificat doivent inclure la clé privée du certificat, car sans la clé privée, un certificat ne peut pas être utilisé pour la restauration de base de données. Ces sauvegardes de clé privée de certificat sont stockés dans un fichier distinct, protégé par un mot de passe doit être fourni pour la restauration de certificat.  
  
## <a name="restoring-the-master-database"></a>Restauration de la base de données master  
La base de données master peut être restaurée à l’aide de **DWConfig**, dans le cadre de la récupération d’urgence.  
  
-   Si le nœud de contrôle n’a pas changé, c'est-à-dire, que si la base de données master est restaurée sur l’appliance inchangée et même à partir de laquelle la sauvegarde de base de données master a été effectuée, la clé DMK et tous les certificats seront lisibles sans action supplémentaire.  
  
-   Si la base de données master est restaurée sur un matériel différent, ou si le nœud de contrôle a été modifié depuis la sauvegarde de la base de données master, les étapes supplémentaires sont nécessaires pour régénérer la clé DMK.  
  
    1.  Ouvrez la clé DMK :  
  
        ```sql  
        OPEN MASTER KEY DECRYPTION BY PASSWORD = '<password>';  
        ```  
  
    2.  Ajouter le chiffrement par clé SMK :  
  
        ```sql  
        ALTER MASTER KEY   
            ADD ENCRYPTION BY SERVICE MASTER KEY;  
        ```  
  
    3.  Redémarrez l’appliance.  
  
## <a name="upgrade-and-replacing-virtual-machines"></a>Mise à niveau et le remplacement des Machines virtuelles  
Si une clé DMK existe sur le matériel sur lequel mise à niveau ou remplacer la machine virtuelle a été effectuée, le mot de passe de clé DMK doit être fourni en tant que paramètre.  
  
Exemple de l’action de mise à niveau. Remplacez `**********` avec votre mot de passe de clé DMK.  
  
`setup.exe /Action=ProvisionUpgrade … DMKPassword='**********'  `  
  
Exemple de l’action pour remplacer un ordinateur virtuel.  
  
`setup.exe /Action=ReplaceVM … DMKPassword='**********'  `  
  
Pendant la mise à niveau, si un utilisateur de base de données est chiffré et le mot de passe de clé n’est pas fourni, l’action de mise à niveau échoue. Au cours de remplacement, si le mot de passe n’est pas fourni lorsqu’une clé DMK existe, l’opération ignorer l’étape de récupération de clé. Toutes les autres étapes seront terminées à la fin de l’action de machine virtuelle de remplacement, toutefois, l’action signalera l’échec à la fin pour indiquer que les étapes supplémentaires sont nécessaires. Dans les journaux d’installation (situé dans **\ProgramData\Microsoft\Microsoft SQL Server Parallel Data Warehouse\100\Logs\Setup\\< horodatage > \Detail-Setup**), l’avertissement suivant s’affichera à la fin.  
  
`*** WARNING \*\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!  `
  
Exécutez ces instruction manuellement dans PDW et redémarrer l’appliance après cela afin de récupérer la clé DMK :  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
Utilisez les étapes de la **restauration de la base de données master** paragraphe pour récupérer la base de données et redémarrez l’appliance.  
  
Si la clé DMK existait avant, mais n’a pas été récupérée après l’action, le message d’erreur suivant est déclenché lorsqu’une base de données est interrogée.  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>Impact sur les performances  
L’impact sur les performances de chiffrement transparent des données varie selon le type de données dont vous disposez, comment il est stocké et le type d’activité de charge de travail sur le serveur SQL Server PDW. Lorsque protégée par TDE, les e/s de lecture et déchiffrement des données ou le chiffrement et écrire des données est une activité intensive du processeur et aura plus d’impact lorsque d’autres activités intensives du processeur sont produisent en même temps. Étant donné que le chiffrement transparent des données chiffre `tempdb`, chiffrement transparent des données peuvent affecter les performances des bases de données qui ne sont pas chiffrés. Pour obtenir une idée précise des performances, vous devez tester l’ensemble du système avec votre activité de données et des requêtes.  
  
## <a name="related-content"></a>Contenu associé  
Les liens suivants contiennent des informations générales sur la manière dont SQL Server gère le chiffrement. Ces articles peuvent vous aider à comprendre le chiffrement de SQL Server, mais que ces articles n’ont pas d’informations spécifiques à SQL Server PDW et ils abordent les fonctionnalités qui ne sont pas présentes dans SQL Server PDW.  
  
-   [Chiffrement SQL Server](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [Hiérarchie de chiffrement](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [SQL Server et clés de chiffrement de base de données](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)  
[CRÉER UNE CLÉ PRINCIPALE](../t-sql/statements/create-master-key-transact-sql.md)  
[CRÉER LA CLÉ DE CHIFFREMENT DE BASE DE DONNÉES](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
