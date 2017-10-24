---
title: DBCC SHRINKFILE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHRINKFILE
- DBCC_SHRINKFILE_TSQL
- DBCC SHRINKFILE
- SHRINKFILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- TRUNCATEONLY option
- shrinking files
- NOTRUNCATE option
- shrinking databases
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
- DBCC SHRINKFILE statement
ms.assetid: e02b2318-bee9-4d84-a61f-2fddcf268c9f
caps.latest.revision: 87
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 14746a5bfac3674299e03b6eba0da1a823f1bba9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-shrinkfile-transact-sql"></a>DBCC SHRINKFILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Réduit la taille du fichier journal ou de données spécifié pour la base de données actuelle, ou vide un fichier en déplaçant les données depuis le fichier spécifié vers d'autres fichiers du même groupe de fichiers, permettant ainsi de supprimer le fichier de la base de données. Vous pouvez réduire un fichier à une taille inférieure à la taille spécifiée lors de sa création. Dans ce cas, la nouvelle valeur correspond à la taille de fichier minimale.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
  
DBCC SHRINKFILE   
(  
    { file_name | file_id }   
    { [ , EMPTYFILE ]   
    | [ [ , target_size ] [ , { NOTRUNCATE | TRUNCATEONLY } ] ]  
    }  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Arguments  
*nom_fichier*  
Nom logique du fichier dont la taille doit être réduite.
  
*FILE_ID*  
Numéro d'identification (ID) du fichier à réduire. Pour obtenir un ID de fichier, utilisez le [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) fonction système ou une requête le [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) vue dans la base de données de catalogue.
  
*target_size*  
Taille en octets du fichier, exprimée sous la forme d'un entier. Si ce paramètre n'est pas spécifié, DBCC SHRINKFILE réduit la taille à la taille de fichier par défaut. La taille par défaut est la taille spécifiée lors de la création du fichier.
  
> [!NOTE]  
>  Vous pouvez réduire la taille par défaut d’un fichier vide à l’aide de DBCC SHRINKFILE *target_size*. Par exemple, si vous créez un fichier de 5 Mo, puis que vous le réduisez à 3 Mo pendant que le fichier est encore vide, la taille de fichier par défaut est fixée à 3 Mo. Cela s'applique uniquement aux fichiers vides qui n'ont jamais contenu des données.  
  
Cette option n'est pas prise en charge pour les conteneurs de groupe de fichiers FILESTREAM.  
Si *target_size* est spécifié, DBCC SHRINKFILE tente de réduire le fichier à la taille spécifiée. Les pages utilisées dans la partie du fichier à libérer sont transférées vers un espace libre disponible dans la partie du fichier conservée. Par exemple, s’il existe un fichier de données de 10 Mo, opérations DBCC SHRINKFILE avec un *target_size* 8 causes toutes les pages utilisées dans les 2 derniers Mo du fichier à être réaffectés dans les pages non allouées dans les 8 premiers Mo du fichier. DBCC SHRINKFILE ne réduit pas un fichier au-delà de la taille nécessaire pour stocker les données dans le fichier. Par exemple, si 7 Mo d’un fichier de données de 10 Mo est utilisé, une instruction DBCC SHRINKFILE avec un *target_size* 6 réduit le fichier à 7 Mo et non pas 6 Mo.
  
EMPTYFILE  
Migre toutes les données à partir du fichier spécifié vers d’autres fichiers dans le **même groupe de fichiers**. En d’autres termes, EmptyFile sera migrer les données à partir du fichier spécifié vers d’autres fichiers dans le même groupe de fichiers. EMPTYFILE vous permet de garantir qu’aucune nouvelle donnée ne figurera dans le fichier. Le fichier peut être supprimé à l’aide de la [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) instruction.
Pour les conteneurs de groupe de fichiers FILESTREAM, le fichier ne peut pas être supprimé à l'aide d'ALTER DATABASE tant que le Garbage collector FILESTREAM n'a pas été exécuté pour supprimer tous les fichiers conteneurs de groupe de fichiers inutiles qu'EMPTYFILE a copiés vers un autre conteneur. Pour plus d’informations, consultez [sp_filestream_force_garbage_collection &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
> [!NOTE]  
>  Pour plus d’informations sur la suppression d’un conteneur FILESTREAM, consultez la section correspondante de [modifier le fichier de base de données et les Options de groupe de fichiers &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
  
NOTRUNCATE  
Déplace des pages allouées à partir de la fin d’un fichier de données vers les pages non allouées du début du fichier avec ou sans *target_size*. L'espace libre à la fin du fichier n'est pas restitué au système d'exploitation et la taille physique du fichier ne change pas. Ainsi, lorsque l'option NOTRUNCATE est spécifiée, le fichier ne paraît pas être réduit.
NOTRUNCATE n'est applicable qu'aux fichiers de données. Les fichiers journaux ne sont pas affectés.   Cette option n'est pas prise en charge pour les conteneurs de groupe de fichiers FILESTREAM.
  
TRUNCATEONLY  
Libère pour le système d'exploitation tout l'espace libre à la fin du fichier, mais n'effectue aucun déplacement de page au sein du fichier. Le fichier de données est réduit seulement jusqu'à la dernière extension allouée.
*target_size* est ignorée si spécifiée avec TRUNCATEONLY.  
L'option TRUNCATEONLY ne déplace pas d'informations dans le journal, mais supprime les fichiers journaux virtuels inactifs de la fin du fichier journal. Cette option n'est pas prise en charge pour les conteneurs de groupe de fichiers FILESTREAM.
  
WITH NO_INFOMSGS  
Supprime tous les messages d'information.
  
## <a name="result-sets"></a>Jeux de résultats  
Le tableau suivant décrit les colonnes du jeu de résultats.
  
|Nom de colonne| Description|  
|---|---|
|**DbId**|Numéro d’identification du fichier de base de données la [!INCLUDE[ssDE](../../includes/ssde-md.md)] a tenté de réduction.|  
|**FileId**|Le numéro d’identification du fichier de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] a tenté de réduction.|  
|**CurrentSize**|Nombre de pages de 8 Ko que le fichier occupe actuellement.|  
|**MinimumSize**|Nombre de pages de 8 Ko que le fichier pourrait occuper au minimum. Ceci correspond à la taille minimale ou à la taille de création d'un fichier.|  
|**UsedPages**|Nombre de pages de 8 Ko que le fichier utilise actuellement.|  
|**EstimatedPages**|Nombre de 8 Ko de pages qui le [!INCLUDE[ssDE](../../includes/ssde-md.md)] le fichier peut être réduit à des estimations.|  
  
## <a name="remarks"></a>Notes  
DBCC SHRINKFILE s'applique aux fichiers de la base de données active. Pour plus d’informations sur la modification de la base de données actuelle, consultez [utiliser &#40; Transact-SQL &#41; ](../../t-sql/language-elements/use-transact-sql.md).
  
Les opérations DBCC SHRINKFILE peuvent être arrêtées à n'importe quel stade du processus, chaque travail terminé étant conservé.
  
Lorsqu’une opération DBCC SHRINKFILE échoue, une erreur est générée.
  
 Il n'est pas nécessaire que la base de données à réduire soit en mode mono-utilisateur ; d'autres utilisateurs peuvent travailler dans la base de données lorsque la taille du fichier est réduite. Il n'est pas nécessaire d'exécuter l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode mono-utilisateur pour réduire les bases de données système.  
  
## <a name="shrinking-a-log-file"></a>Réduction d'un fichier journal  
Pour les fichiers journaux, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise *target_size* pour calculer la taille cible pour l’ensemble du journal ; par conséquent, *target_size* est la quantité d’espace libre dans le journal après l’opération de réduction. La taille cible de l'ensemble du journal est ensuite convertie dans la taille cible de chaque fichier journal. DBCC SHRINKFILE tente de ramener immédiatement la taille de chaque fichier journal physique à la taille cible. Toutefois, si la partie du journal logique se trouve dans les journaux virtuels au-delà de la taille cible, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] libère autant d’espace que possible et émet alors un message d’information. Le message décrit les actions à effectuer pour déplacer le journal logique à partir des journaux virtuels à la fin du fichier. Lorsque les actions sont effectuées, DBCC SHRINKFILE peut être utilisé pour libérer l'espace restant.
  
Comme un fichier journal ne peut être réduit que jusqu'à une limite virtuelle, il arrive qu'il ne soit pas possible de réduire un fichier journal à une taille inférieure à celle d'un fichier journal virtuel, même s'il n'est pas utilisé. La taille du fichier journal virtuel est choisie dynamiquement par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au moment de la création ou de l'extension des fichiers journaux.
  
## <a name="best-practices"></a>Bonnes pratiques  
Prenez en compte les informations suivantes lorsque vous envisagez de réduire un fichier :
-   Une opération de réduction de taille de fichier est plus efficace après l'exécution d'une opération qui crée une grande quantité d'espace inutilisé, telle qu'une troncature de table ou une suppression de table.  
-   Un certain espace libre doit exister pour les opérations quotidiennes courantes pour la plupart des bases de données. Si vous réduisez plusieurs fois la taille d'une base de données et que vous constatez que la taille augmente de nouveau, cela indique que l'espace qui a été réduit est nécessaire pour les opérations courantes. Dans ce cas, la réduction de la taille de la base de données ne sert à rien.  
-   Une opération de réduction ne conserve pas l'état de fragmentation des index de la base de données, et augmente généralement la fragmentation. Il s'agit là d'une raison supplémentaire pour ne pas réduire la taille de la base de données de manière répétitive.  
-   Réduisez plusieurs fichiers dans la même base de données de manière séquentielle plutôt que simultanément. La contention sur les tables système peut entraîner des délais en raison de blocage.  
  
## <a name="troubleshooting"></a>Dépannage  
Cette section décrit comment diagnostiquer et corriger les problèmes qui peuvent se produire lors de l'exécution de la commande DBCC SHRINKFILE.
  
### <a name="the-file-does-not-shrink"></a>La taille du fichier n'est pas réduite  
Si l'opération de réduction s'exécute sans erreur, mais que la taille du fichier ne semble pas avoir changé, vérifiez que le fichier dispose d'un espace adéquat à supprimer, en effectuant l'une des opérations suivantes :
- Exécutez la requête suivante.  
  
```sql
SELECT name ,size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 AS AvailableSpaceInMB
FROM sys.database_files;
```

-   Exécutez le [DBCC SQLPERF](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md) commande pour retourner l’espace utilisé dans le journal des transactions.  
Si l'espace disponible est insuffisant, l'opération de réduction ne peut pas réduire davantage la taille du fichier.
  
En règle générale, c'est la taille du fichier journal qui semble impossible à réduire. Ceci est généralement dû à un fichier journal qui n'a pas été tronqué. Vous pouvez tronquer le journal en attribuant la valeur SIMPLE au mode de récupération de base de données, ou en sauvegardant le journal et en réexécutant l'opération DBCC SHRINKFILE.
  
### <a name="the-shrink-operation-is-blocked"></a>L'opération de réduction est bloquée  
Il est possible pour les opérations de réduction soient bloquées par une transaction qui s’exécute sous un [niveau d’isolement basé sur le contrôle de version de ligne](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md). Par exemple, si une importante opération de suppression exécutée sous un niveau d'isolation basé sur le contrôle de version de ligne se déroule parallèlement à une opération DBCC SHRINK DATABASE, l'opération de réduction attendra la fin de l'opération de suppression pour réduire la taille des fichiers. Dans ce cas, les opérations DBCC SHRINKFILE et DBCC SHRINKDATABASE envoient un message d'information (5202 pour SHRINKDATABASE et 5203 pour SHRINKFILE) dans le journal des erreurs de SQL Server toutes les cinq minutes au cours de la première heure, puis toutes les heures. Par exemple, si le journal des erreurs contient le message d'erreur suivant, l'erreur suivante se produit :
  
```sql
DBCC SHRINKFILE for file ID 1 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
cela signifie que l'opération de réduction est bloquée par des transactions d'instantané ayant des valeurs d'horodateur plus anciennes que 109, qui est le numéro de la dernière transaction que l'opération de réduction a effectuée. Il indique également que le **transaction_sequence_num**, ou **first_snapshot_sequence_num** colonnes dans le [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) vue de gestion dynamique contient une valeur de 15. Si le **transaction_sequence_num**, ou **first_snapshot_sequence_num** colonnes dans la vue contient un nombre qui est inférieur à la dernière transaction effectuée par une opération de réduction (109), l’opération de réduction attendra que ces transactions soient terminées.
  
Pour résoudre ce problème, vous pouvez effectuer l'une des opérations suivantes :
-   Achevez la transaction qui bloque l'opération de réduction.
-   Achevez l'opération de réduction. Si vous achevez l'opération de réduction, tout travail accompli est conservé.  
-   Laissez simplement l'opération de réduction attendre que la transaction bloquante s'achève.  
  
## <a name="permissions"></a>Permissions  
Nécessite l’appartenance au rôle de serveur fixe **sysadmin** ou au rôle de base de données fixe **db_owner** .
  
## <a name="examples"></a>Exemples  
  
### <a name="a-shrinking-a-data-file-to-a-specified-target-size"></a>A. Réduction d'un fichier de données à une taille cible spécifiée  
L’exemple suivant réduit la taille d’un fichier de données nommé `DataFile1` dans les `UserDB` base de données utilisateur à 7 Mo.
  
```sql  
USE UserDB;  
GO  
DBCC SHRINKFILE (DataFile1, 7);  
GO  
```  
  
### <a name="b-shrinking-a-log-file-to-a-specified-target-size"></a>B. Réduction d'un fichier journal à une taille cible spécifiée  
L'exemple suivant ramène la taille du fichier journal de la base de données `AdventureWorks` à 1 Mo. Pour que la commande DBCC SHRINKFILE puisse réduire la taille du fichier, le système tronque d'abord celui-ci en attribuant la valeur SIMPLE au mode de récupération de base de données.
  
```sql  
USE AdventureWorks2012;  
GO  
-- Truncate the log by changing the database recovery model to SIMPLE.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY SIMPLE;  
GO  
-- Shrink the truncated log file to 1 MB.  
DBCC SHRINKFILE (AdventureWorks2012_Log, 1);  
GO  
-- Reset the database recovery model.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL;  
GO  
```  
  
### <a name="c-truncating-a-data-file"></a>C. Troncation d'un fichier de données  
L'exemple suivant tronque le fichier de données primaire dans la base de données `AdventureWorks`. Le système interroge l'affichage catalogue `sys.database_files` afin d'obtenir la valeur `file_id` du fichier de données.
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name  
FROM sys.database_files;  
GO  
DBCC SHRINKFILE (1, TRUNCATEONLY);  
```  
  
### <a name="d-emptying-a-file"></a>D. Vidage d'un fichier  
L'exemple suivant illustre la procédure qui permet de vider un fichier de manière à ce qu'il puisse être supprimé de la base de données. Pour que cet exemple fonctionne, un fichier de données est d'abord créé et celui-ci est censé contenir des données.
  
```sql  
USE AdventureWorks2012;  
GO  
-- Create a data file and assume it contains data.  
ALTER DATABASE AdventureWorks2012   
ADD FILE (  
    NAME = Test1data,  
    FILENAME = 'C:\t1data.ndf',  
    SIZE = 5MB  
    );  
GO  
-- Empty the data file.  
DBCC SHRINKFILE (Test1data, EMPTYFILE);  
GO  
-- Remove the data file from the database.  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE Test1data;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)  
[FILE_ID &#40; Transact-SQL &#41;](../../t-sql/functions/file-id-transact-sql.md)  
[sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[Réduire un fichier](../../relational-databases/databases/shrink-a-file.md)
  
  

