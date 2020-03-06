---
title: Chiffrement transparent des données
description: Le chiffrement transparent des données (TDE) pour les Data Warehouse parallèles (PDW) effectue un chiffrement et un déchiffrement en temps réel des données et des fichiers journaux des transactions et des fichiers journaux PDW spéciaux.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: e75230ed175c6fbf1b0a2492265bbe12067060ca
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78339737"
---
# <a name="transparent-data-encryption"></a>chiffrement transparent des données
Vous pouvez prendre plusieurs précautions pour sécuriser la base de données telles que la conception d’un système sécurisé, le chiffrement de ressources confidentielles et la création d'un pare-feu autour des serveurs de base de données. Toutefois, pour un scénario dans lequel le support physique (tel que des lecteurs ou des bandes de sauvegarde) est volé, une partie malveillante peut simplement restaurer ou attacher la base de données et parcourir les données. Une solution consiste à chiffrer les données sensibles dans la base de données et à protéger les clés utilisées pour chiffrer les données avec un certificat. Cela empêche toute personne qui ne dispose pas des clés d'utiliser les données, mais ce type de protection doit être planifié à l'avance.  
  
Le *chiffrement transparent des données* (TDE) effectue un chiffrement et un déchiffrement en temps réel des données et des fichiers journaux des transactions et des fichiers journaux PDW spéciaux. Le chiffrement utilise une clé de chiffrement de base de données stockée dans l’enregistrement de démarrage de base de données à des fins de disponibilité lors de la récupération. Le DEK est une clé symétrique sécurisée à l’aide d’un certificat stocké dans la base de données Master de la SQL Server PDW. Le chiffrement transparent des données protège les données « au repos », autrement dit les fichiers de données et les fichiers journaux. Il permet de se conformer à de nombreuses lois, règles et instructions établies dans différents secteurs professionnels. Cette fonctionnalité permet aux développeurs de logiciels de chiffrer des données à l’aide d’algorithmes de chiffrement AES et 3DES sans modifier les applications existantes.  
  
> [!IMPORTANT]  
> TDE ne fournit pas de chiffrement pour les données circulant entre le client et le PDW. Pour plus d’informations sur le chiffrement des données entre le client et le SQL Server PDW, consultez [approvisionner un certificat](provision-certificate.md).  
>   
> TDE ne chiffre pas les données lorsqu’elles sont en cours de déplacement ou en cours d’utilisation. Le trafic interne entre les composants PDW à l’intérieur du SQL Server PDW n’est pas chiffré. Les données stockées temporairement dans des mémoires tampons ne sont pas chiffrées. Pour limiter ce risque, contrôlez l’accès physique et les connexions au SQL Server PDW.  
  
Une fois sécurisée, la base de données peut être restaurée à l'aide du certificat approprié.  
  
> [!NOTE]  
> Lorsque vous créez un certificat pour TDE, vous devez immédiatement le sauvegarder, ainsi que la clé privée associée. Dans l'éventualité où le certificat ne serait plus disponible ou que vous deviez restaurer ou attacher la base de données sur un autre serveur, vous devez disposer de sauvegardes du certificat et de la clé privée, sans quoi vous ne pourrez pas ouvrir la base de données. Le certificat de chiffrement doit être conservé même si le chiffrement transparent des données n'est plus activé sur la base de données. Même si la base de données n'est pas chiffrée, des parties du journal des transactions peuvent toujours être protégées, et le certificat peut être nécessaire pour certaines opérations tant que la sauvegarde complète de la base de données n'a pas été effectuée. Un certificat qui a dépassé sa date d'expiration peut toujours être utilisé pour chiffrer et déchiffrer les données avec le chiffrement transparent des données.  
  
Le chiffrement du fichier de base de données est effectué au niveau de la page. Les pages d'une base de données chiffrée sont chiffrées avant d'être écrites sur le disque et déchiffrées lorsqu'elles sont lues en mémoire. Le chiffrement transparent des données n'augmente pas la taille de la base de données chiffrée.  
  
L’illustration suivante montre la hiérarchie des clés pour le chiffrement TDE :  
  
![Affiche la hiérarchie](media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-tde"></a>Utilisation du chiffrement transparent des données  
Pour utiliser le chiffrement transparent des données, procédez comme suit : Les trois premières étapes ne sont effectuées qu’une seule fois, lors de la préparation de SQL Server PDW pour prendre en charge TDE.  
  
1.  Créez une clé principale dans la base de données Master.  
  
2.  Utilisez **sp_pdw_database_encryption** pour activer TDE sur le SQL Server PDW. Cette opération modifie les bases de données temporaires afin de garantir la protection des futures données temporaires et échouera si une tentative est effectuée alors que des sessions actives comportent des tables temporaires. **sp_pdw_database_encryption** active le masquage des données utilisateur dans les journaux système PDW. (Pour plus d’informations sur le masquage des données utilisateur dans les journaux système PDW, consultez [sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md).)  
  
3.  Utilisez [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) pour créer des informations d’identification qui peuvent s’authentifier et écrire sur le partage où sera stockée la sauvegarde du certificat. S’il existe déjà des informations d’identification pour le serveur de stockage prévu, vous pouvez utiliser les informations d’identification existantes.  
  
4.  Dans la base de données Master, créez un certificat protégé par la clé principale.  
  
5.  Sauvegardez le certificat dans le partage de stockage.  
  
6.  Dans la base de données utilisateur, créez une clé de chiffrement de base de données et protégez-la par le certificat stocké dans la base de données Master.  
  
7.  Utilisez l' `ALTER DATABASE` instruction pour chiffrer la base de données à l’aide de TDE.  
  
L’exemple suivant illustre le chiffrement de `AdventureWorksPDW2012` la base de données à `MyServerCert`l’aide d’un certificat nommé, créé dans SQL Server PDW.  
  
**Tout d’abord : activez TDE sur le SQL Server PDW.** Cette action n’est nécessaire qu’une seule fois.  
  
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
  
**Deuxièmement : créez et sauvegardez un certificat dans la base de données Master.** Cette action n’est requise qu’une seule fois. Vous pouvez avoir un certificat distinct pour chaque base de données (recommandé), ou vous pouvez protéger plusieurs bases de données à l’aide d’un seul certificat.  
  
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
  
**Dernière : créez le DEK et utilisez ALTER DATABASE pour chiffrer une base de données utilisateur.** Cette action est répétée pour chaque base de données protégée par TDE.  
  
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
  
Les opérations de chiffrement et de déchiffrement sont planifiées sur les threads d’arrière-plan par SQL Server. Vous pouvez afficher l’état de ces opérations à l’aide des affichages catalogue et des vues de gestion dynamique dans la liste qui s’affiche plus loin dans cet article.  
  
> [!CAUTION]  
> Les fichiers de sauvegarde des bases de données pour lesquelles le chiffrement transparent des données est activé sont également chiffrés à l'aide de la clé de chiffrement de base de données. En conséquence, lorsque vous restaurez ces sauvegardes, le certificat qui protège la clé de chiffrement de base de données doit être disponible. Cela signifie qu'en plus de sauvegarder la base de données, vous devez vous assurer que vous conservez des sauvegardes des certificats du serveur pour empêcher toute perte de données. Une perte de données interviendra si le certificat n'est plus disponible.  
  
## <a name="commands-and-functions"></a>Commandes et fonctions  
Les certificats TDE doivent être chiffrés par la clé principale de base de données pour être acceptés par les instructions suivantes.  
  
Le tableau suivant fournit des liens et des explications pour les commandes et les fonctions TDE.  
  
|Commande ou fonction|Objectif|  
|-----------------------|-----------|  
|[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)|Crée une clé permettant de chiffrer une base de données.|  
|[ALTER DATABASE ENCRYPTION KEY](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|Modifie la clé qui permet de chiffrer une base de données.|  
|[SUPPRIMER LA CLÉ DE CHIFFREMENT DE BASE DE DONNÉES](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|Supprime la clé qui était utilisée pour chiffrer une base de données.|  
|[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)|Présente l'option **ALTER DATABASE** qui est utilisée pour activer le chiffrement transparent des données.|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>Affichages catalogue et vues de gestion dynamique  
Le tableau suivant indique les affichages catalogue et les vues de gestion dynamique du chiffrement transparent des données.  
  
|Affichage catalogue ou vue de gestion dynamique|Objectif|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|Affichage catalogue qui affiche des informations sur la base de données.|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|Affichage catalogue qui indique les certificats inclus dans une base de données.|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|Vue de gestion dynamique qui fournit des informations pour chaque nœud, sur les clés de chiffrement utilisées dans une base de données et sur l’état du chiffrement d’une base de données.|  
  
## <a name="permissions"></a>Autorisations  
Chaque fonctionnalité et commande TDE requiert des autorisations individuelles, décrites dans les tableaux précédents.  
  
L’affichage des métadonnées impliquées dans TDE `CONTROL SERVER` nécessite l’autorisation.  
  
## <a name="considerations"></a>Considérations  
Lorsqu'une analyse de rechiffrement est en cours pour une opération de chiffrement de la base de données, les opérations de maintenance sur la base de données sont désactivées.  
  
Vous pouvez trouver l’état du chiffrement de la base de données à l’aide de la vue de gestion dynamique **sys. dm_pdw_nodes_database_encryption_keys** . Pour plus d’informations, consultez la section *affichages catalogue et vues de gestion dynamique* plus haut dans cet article.  
  
### <a name="restrictions"></a>Restrictions  
Les opérations suivantes ne sont pas autorisées au `CREATE DATABASE ENCRYPTION KEY`cours `ALTER DATABASE ENCRYPTION KEY`des `DROP DATABASE ENCRYPTION KEY`instructions, `ALTER DATABASE...SET ENCRYPTION` , ou.  
  
-   Suppression de la base de données  
  
-   Utilisation d' `ALTER DATABASE` une commande.  
  
-   Démarrage d’une sauvegarde de base de données.  
  
-   Démarrage d’une restauration de base de données.  
  
Les opérations ou conditions suivantes empêchent `CREATE DATABASE ENCRYPTION KEY`les `ALTER DATABASE ENCRYPTION KEY`instructions `DROP DATABASE ENCRYPTION KEY`,, `ALTER DATABASE...SET ENCRYPTION` ou.  
  
-   Une `ALTER DATABASE` commande est en cours d’exécution.  
  
-   Une sauvegarde de données est en cours d'exécution.  
  
Lors de la création de fichiers de base de données, l'initialisation instantanée des fichiers n'est pas disponible lorsque le chiffrement transparent des données est activé.  
  
### <a name="areas-not-protected-by-tde"></a>Zones non protégées par TDE  
TDE ne protège pas les tables externes.  
  
TDE ne protège pas les sessions de diagnostic. Les utilisateurs doivent veiller à ne pas interroger des paramètres sensibles alors que les sessions de diagnostic sont en cours d’utilisation. Les sessions de diagnostic qui révèlent des informations sensibles doivent être supprimées dès qu’elles ne sont plus nécessaires.  
  
Les données protégées par TDE sont déchiffrées lorsqu’elles sont placées en mémoire SQL Server PDW. Des vidages de mémoire sont créés lorsque certains problèmes se produisent sur l’appliance. Les fichiers de vidage représentent le contenu de la mémoire au moment de l’apparition du problème et peuvent contenir des données sensibles dans un format non chiffré. Le contenu des images mémoire doit être examiné avant d’être partagé avec d’autres utilisateurs.  
  
La base de données Master n’est pas protégée par TDE. Bien que la base de données Master ne contienne pas de données utilisateur, elle contient des informations telles que les noms de connexion.  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Chiffrement transparent des données et journaux de transactions  
L’activation d’une base de données pour l’utilisation de TDE a pour effet de replacer la partie restante du journal des transactions virtuelles afin de forcer le prochain journal des transactions virtuelles. Cela garantit qu'aucun texte en clair n'est conservé dans les journaux des transactions après que la base de données a été définie pour le chiffrement. Vous pouvez rechercher l’état du chiffrement du fichier journal sur chaque nœud PDW en affichant `encryption_state` la colonne dans `sys.dm_pdw_nodes_database_encryption_keys` la vue, comme dans cet exemple :  
  
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
SQL Server PDW gère un ensemble de journaux destinés à la résolution des problèmes. (Notez qu’il ne s’agit pas du journal des transactions, du SQL Server journal des erreurs ou du journal des événements Windows.) Ces journaux d’activité PDW peuvent contenir des instructions complètes en texte clair, dont certaines peuvent contenir des données utilisateur. Les instructions **Insert** et **Update** sont des exemples typiques. Le masquage des données utilisateur peut être explicitement activé ou désactivé à l’aide de **sp_pdw_log_user_data_masking**. L’activation du chiffrement sur SQL Server PDW active automatiquement le masquage des données utilisateur dans les journaux d’activité PDW afin de les protéger. **sp_pdw_log_user_data_masking** peut également être utilisé pour masquer des instructions si vous n’utilisez pas TDE, mais cela n’est pas recommandé, car cela réduit considérablement la capacité de l’équipe support Microsoft à analyser les problèmes.  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Chiffrement transparent des données et base de données système tempdb  
La base de données système tempdb est chiffrée lorsque le chiffrement est activé à l’aide de [sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md). Cela est nécessaire pour qu’une base de données puisse utiliser TDE. Cela peut avoir un effet sur les performances des bases de données non chiffrées sur la même instance de SQL Server PDW.  
  
## <a name="key-management"></a>Gestion des clés  
La clé de chiffrement de base de données (DEK) est protégée par les certificats stockés dans la base de données Master. Ces certificats sont protégés par la clé principale de base de données (DMK) de la base de données Master. Le DMK doit être protégé par la clé principale du service (SMK) afin d’être utilisé pour TDE.  
  
Le système peut accéder aux clés sans nécessiter une intervention humaine (comme fournir un mot de passe). Si le certificat n’est pas disponible, le système génère une erreur qui explique que le DEK ne peut pas être déchiffré tant que le certificat approprié n’est pas disponible.  
  
Lors du déplacement d’une base de données d’une appliance vers une autre, le certificat utilisé pour protéger son « DEK » doit d’abord être restauré sur le serveur de destination. La base de données peut ensuite être restaurée comme d’habitude. Pour plus d’informations, consultez la documentation de SQL Server standard, à la page [déplacer une base de données protégée TDE vers une autre SQL Server](https://technet.microsoft.com/library/ff773063.aspx).  
  
Les certificats utilisés pour chiffrer les chiffrement doivent être conservés tant qu’il existe des sauvegardes de base de données qui les utilisent. Les sauvegardes de certificats doivent inclure la clé privée du certificat, car sans la clé privée, un certificat ne peut pas être utilisé pour la restauration de la base de données. Ces sauvegardes de clés privées de certificat sont stockées dans un fichier distinct, protégé par un mot de passe qui doit être fourni pour la restauration des certificats.  
  
## <a name="restoring-the-master-database"></a>Restauration de la base de données Master  
La base de données Master peut être restaurée à l’aide de **DWConfig**, dans le cadre de la récupération d’urgence.  
  
-   Si le nœud de contrôle n’a pas changé, c’est-à-dire si la base de données Master est restaurée sur l’appliance identique et non modifiée à partir de laquelle la sauvegarde de la base de données Master a été effectuée, les DMK et tous les certificats seront lisibles sans action supplémentaire.  
  
-   Si la base de données Master est restaurée sur une autre appliance ou si le nœud de contrôle a été modifié depuis la sauvegarde de la base de données Master, des étapes supplémentaires sont nécessaires pour régénérer le DMK.  
  
    1.  Ouvrez le DMK :  
  
        ```sql  
        OPEN MASTER KEY DECRYPTION BY PASSWORD = '<password>';  
        ```  
  
    2.  Ajoutez le chiffrement par SMK :  
  
        ```sql  
        ALTER MASTER KEY   
            ADD ENCRYPTION BY SERVICE MASTER KEY;  
        ```  
  
    3.  Redémarrez l’appliance.  
  
## <a name="upgrade-and-replacing-virtual-machines"></a>Mettre à niveau et remplacer des machines virtuelles  
Si un DMK existe sur l’appliance sur lequel la mise à niveau ou le remplacement d’une machine virtuelle a été effectuée, le mot de passe DMK doit être fourni en tant que paramètre.  
  
Exemple de l’action de mise à niveau. Remplacez `**********` par votre mot de passe DMK.  
  
`setup.exe /Action=ProvisionUpgrade ... DMKPassword='**********'`  
  
Exemple de l’action pour remplacer un ordinateur virtuel.  
  
`setup.exe /Action=ReplaceVM ... DMKPassword='**********'`  
  
Pendant la mise à niveau, si une base de donnée utilisateur est chiffrée et que le mot de passe DMK n’est pas fourni, l’action de mise à niveau échoue. Lors du remplacement, si le mot de passe approprié n’est pas fourni lorsqu’un DMK existe, l’opération ignore l’étape de récupération DMK. Toutes les autres étapes seront effectuées à la fin de l’action remplacer l’ordinateur virtuel, mais l’action signalera une erreur à la fin pour indiquer que des étapes supplémentaires sont requises. Dans les journaux d’installation (situés dans **\ProgramData\Microsoft\Microsoft SQL Server Parallel Data\\ Warehouse\100\Logs\Setup<> \detail-Setup**), l’avertissement suivant s’affiche près de la fin.  
  
`*** WARNING \*\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!`
  
Exécutez l’instruction manuellement dans PDW et redémarrez l’appliance après cela pour récupérer DMK :  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
Utilisez les étapes du paragraphe **restauration de la base de données Master** pour récupérer la base de données, puis redémarrez l’appliance.  
  
Si le DMK existait avant mais n’a pas été récupéré après l’action, le message d’erreur suivant est déclenché lors de l’interrogation d’une base de données.  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>Impact sur les performances  
L’impact sur les performances de TDE varie selon le type de données dont vous disposez, la manière dont il est stocké et le type d’activité de charge de travail sur le SQL Server PDW. En cas de protection par TDE, les e/s de lecture et de déchiffrement des données, ou le chiffrement, puis l’écriture des données, sont une activité gourmande en ressources processeur et ont un impact plus important lorsque d’autres activités gourmandes en ressources processeur se produisent en même temps. Étant donné que TDE `tempdb`chiffre, TDE peut affecter les performances des bases de données qui ne sont pas chiffrées. Pour obtenir une idée précise des performances, vous devez tester l’ensemble du système à l’aide de vos données et de votre activité de requête.  
  
## <a name="related-content"></a>Contenu associé  
Les liens suivants contiennent des informations générales sur la façon dont SQL Server gère le chiffrement. Ces articles peuvent vous aider à comprendre le chiffrement SQL Server, mais ces articles n’ont pas d’informations spécifiques à SQL Server PDW et ils discutent des fonctionnalités qui ne sont pas présentes dans SQL Server PDW.  
  
-   [Chiffrement SQL Server](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [Hiérarchie de chiffrement](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [SQL Server et clés de chiffrement de base de données](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md)  
[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
