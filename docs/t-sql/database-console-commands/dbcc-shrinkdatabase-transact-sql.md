---
title: DBCC SHRINKDATABASE (Transact-SQL) | Documents Microsoft
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
- DBCC_SHRINKDATABASE_TSQL
- DBCC SHRINKDATABASE
- SHRINKDATABASE_TSQL
- SHRINKDATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- shrinking files
- shrinking databases
- DBCC SHRINKDATABASE statement
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
ms.assetid: fc976afd-1edb-4341-bf41-c4a42a69772b
caps.latest.revision: 62
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7f6e9fa3feea20bfeb82037cb9358370c67aaa0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-shrinkdatabase-transact-sql"></a>DBCC SHRINKDATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Réduit la taille des fichiers de données et journaux dans la base de données spécifiée.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DBCC SHRINKDATABASE   
( database_name | database_id | 0   
     [ , target_percent ]   
     [ , { NOTRUNCATE | TRUNCATEONLY } ]   
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name* | *database_id* | 0  
 Nom ou identificateur de la base de données à réduire. Si 0 est spécifié, la base de données active est utilisée.  
  
 *target_percent*  
 Pourcentage d'espace que vous voulez laisser disponible dans le fichier de la base de données après sa réduction.  
  
 NOTRUNCATE  
 Compacte les données des fichiers de données en déplaçant les pages allouées de la fin du fichier vers les pages non allouées du début du fichier. *target_size* est facultatif.  
  
 L'espace libre à la fin du fichier n'est pas restitué au système d'exploitation et la taille physique du fichier ne change pas. Ainsi, lorsque l'option NOTRUNCATE est spécifiée, la base de données ne paraît pas être réduite.  
  
 NOTRUNCATE n'est applicable qu'aux fichiers de données. Le fichier journal n'est pas affecté.  
  
 TRUNCATEONLY  
 Libère pour le système d'exploitation tout l'espace libre à la fin du fichier, mais n'effectue aucun déplacement de page au sein du fichier. Le fichier de données est réduit seulement jusqu'à la dernière extension allouée. *target_size* est ignorée si spécifiée avec TRUNCATEONLY.  
  
 TRUNCATEONLY affecte le fichier journal. Pour tronquer uniquement le fichier de données, utilisez DBCC SHRINKFILE.  
  
 WITH NO_INFOMSGS  
 Supprime tous les messages d'information dont les niveaux de gravité sont compris entre 0 et 10.  
  
## <a name="result-sets"></a>Jeux de résultats  
Le tableau suivant décrit les colonnes du jeu de résultats.
  
|Nom de colonne| Description|  
|-----------------|-----------------|  
|**DbId**|Numéro d’identification du fichier de base de données la [!INCLUDE[ssDE](../../includes/ssde-md.md)] a tenté de réduction.|  
|**FileId**|Numéro d’identification du fichier de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] a tenté de réduction.|  
|**CurrentSize**|Nombre de pages de 8 Ko que le fichier occupe actuellement.|  
|**MinimumSize**|Nombre de pages de 8 Ko que le fichier pourrait occuper au minimum. Ceci correspond à la taille minimale ou à la taille de création d'un fichier.|  
|**UsedPages**|Nombre de pages de 8 Ko que le fichier utilise actuellement.|  
|**EstimatedPages**|Nombre de 8 Ko de pages qui le [!INCLUDE[ssDE](../../includes/ssde-md.md)] le fichier peut être réduit à des estimations.|  
  
>[!NOTE]
> Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’affiche pas les lignes pour ces fichiers ne pas réduits.  
  
## <a name="remarks"></a>Notes  
Pour réduire tous les fichiers de données et fichiers journaux d'une base de données particulière, exécutez la commande DBCC SHRINKDATABASE. Pour augmenter ou diminuer les données d’un fichier journal à la fois pour une base de données spécifique, exécutez le [DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) commande.
  
Pour afficher la quantité actuelle de l’espace libre (non alloué) dans la base de données, exécutez [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md).
  
Les opérations DBCC SHRINKDATABASE peuvent être arrêtées à n'importe quel stade du processus, chaque travail terminé étant conservé.
  
La base de données ne peut pas être réduite à une taille inférieure à la taille minimale de la base de données. La taille minimale correspond à la taille spécifiée lors de la création initiale de la base de données ou à la dernière taille explicitement spécifiée à l'aide d'une opération de modification de taille de fichier, notamment en utilisant l'instruction DBCC SHRINKFILE ou ALTER DATABASE. Par exemple, si une base de données est créée à l’origine avec une taille de 10 Mo en taille et a atteint 100 Mo, la plus petite que la base de données peut être réduit à est de 10 Mo, même si toutes les données dans la base de données a été supprimé.
  
Exécuter DBCC SHRINKDATABASE sans spécifier l'option NOTRUNCATE ou TRUNCATEONLY revient à exécuter une opération DBCC SHRINKDATABASE avec NOTRUNCATE suivie d'une opération DBCC SHRINKDATABASE avec TRUNCATEONLY.
  
Il n'est pas nécessaire que la base de données réduite soit mono-utilisateur ; d'autres utilisateurs peuvent travailler sur cette base au cours de l'opération. Ceci inclut également les bases de données système.
  
Vous ne pouvez pas réduire la taille d'une base de données en cours de sauvegarde. Inversement, vous ne pouvez pas sauvegarder une base de données alors qu'elle fait l'objet d'une opération de réduction.
  
## <a name="how-dbcc-shrinkdatabase-works"></a>Fonctionnement de DBCC SHRINKDATABASE  
DBCC SHRINKDATABASE réduit les fichiers de données, fichier par fichier, mais réduit les fichiers journaux comme si tous les fichiers journaux existaient dans un groupe de journaux contigus. Les fichiers sont toujours réduits à partir de la fin.
  
Supposons une base de données nommée **mydb** avec un fichier de données et deux fichiers journaux. Les données et fichiers journaux sont 10 Mo et le fichier de données contient 6 Mo de données.
  
Pour chaque fichier, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcule une taille cible, qui est la taille à laquelle le fichier doit être réduit. Lorsque DBCC SHRINKDATABASE est spécifié avec *target_size*, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcule la taille cible pour être le *target_size* quantité d’espace libre dans le fichier après réduction. Par exemple, si vous spécifiez un *target_size* 25 afin de réduire **mydb**, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcule la taille cible pour le fichier de données être de 8 Mo (6 Mo de données plus 2 Mo d’espace libre). Par conséquent, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] déplace toutes les données dans les 2 derniers Mo du fichier de données vers l’espace libre dans les 8 premiers Mo du fichier de données, puis réduit le fichier.
  
Supposons que le fichier de données de **mydb** contient 7 Mo de données. En spécifiant un *target_size* 30 permet pour ce fichier de données à réduire le pourcentage gratuit de 30. Toutefois, en spécifiant un *target_size* de 40 ne réduit pas le fichier de données, car le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’est pas réduire un fichier à une taille plus petite que les données actuellement présentes. Vous pouvez également considérer ce problème une autre façon : 40 pour cent d’espace libre souhaité ajoutés + le fichier de données complet de 70 pour cent (7 Mo sur 10 Mo) est supérieure à 100 %. Étant donné que le pourcentage d’espace libre souhaité plus le pourcentage actuel occupé par les données est supérieure à 100 pour cent (par 10 pour cent), tout *target_size* supérieure à 30 ne peut pas réduire le fichier de données.
  
Pour les fichiers journaux, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise *target_size* pour calculer la taille cible pour l’ensemble du journal ; par conséquent, *target_size* est la quantité d’espace libre dans le journal après l’opération de réduction. La taille cible pour le journal complet est alors convertie en taille cible pour chaque fichier journal.
  
DBCC SHRINKDATABASE essaie immédiatement de réduire chaque fichier journal physique à sa taille cible. Si aucune partie du journal logique ne se trouve dans les journaux virtuels au-delà de la taille cible du fichier journal, le fichier est tronqué avec succès et DBCC SHRINKDATABASE s'exécute normalement sans émettre de messages. Toutefois, si la partie du journal logique se trouve dans les journaux virtuels au-delà de la taille cible, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] libère autant d’espace que possible et émet alors un message d’information. Le message décrit les actions à effectuer pour déplacer le journal logique à partir des journaux virtuels à la fin du fichier. Lorsque les actions sont effectuées, DBCC SHRINKDATABASE peut être utilisé pour libérer l'espace restant.
  
Comme un fichier journal ne peut être réduit que jusqu'à une limite virtuelle, il arrive qu'il ne soit pas possible de réduire un fichier journal à une taille inférieure à celle d'un fichier journal virtuel, même s'il n'est pas utilisé. La taille du fichier journal virtuel est choisie dynamiquement par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au moment de la création ou de l'extension des fichiers journaux.
  
## <a name="best-practices"></a>Bonnes pratiques  
Prenez en compte les informations suivantes lorsque vous envisagez de réduire une base de données :
-   Une opération de réduction de taille de fichier est plus efficace après l'exécution d'une opération qui crée une grande quantité d'espace inutilisé, telle qu'une troncature de table ou une suppression de table.  
-   Un certain espace libre doit exister pour les opérations quotidiennes courantes pour la plupart des bases de données. Si vous réduisez plusieurs fois la taille d'une base de données et que vous constatez que la taille augmente de nouveau, cela indique que l'espace qui a été réduit est nécessaire pour les opérations courantes. Dans ce cas, la réduction de la taille de la base de données ne sert à rien.  
-   Une opération de réduction ne conserve pas l'état de fragmentation des index de la base de données, et augmente généralement la fragmentation. Il s'agit là d'une raison supplémentaire pour ne pas réduire la taille de la base de données de manière répétitive.  
-   Sauf en cas de besoin précis, n'attribuez pas la valeur ON à l'option de base de données AUTO_SHRINK.  
  
## <a name="troubleshooting"></a>Dépannage  
 Il est possible pour les opérations de réduction soient bloquées par une transaction qui s’exécute sous un [niveau d’isolement basé sur le contrôle de version de ligne](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md). Par exemple, si une importante opération de suppression exécutée sous un niveau d'isolation basé sur le contrôle de version de ligne se déroule parallèlement à une opération DBCC SHRINK DATABASE, l'opération de réduction attendra la fin de l'opération de suppression pour réduire la taille des fichiers. Dans ce cas, les opérations DBCC SHRINKFILE et DBCC SHRINKDATABASE envoient un message d'information (5202 pour SHRINKDATABASE et 5203 pour SHRINKFILE) dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] toutes les cinq minutes au cours de la première heure, puis toutes les heures. Par exemple, si le journal des erreurs contient le message d'erreur :  
  
```sql
DBCC SHRINKDATABASE for database ID 9 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
cela signifie que l'opération de réduction est bloquée par des transactions d'instantané ayant des valeurs d'horodateur plus anciennes que 109, qui est le numéro de la dernière transaction que l'opération de réduction a effectuée. Il indique également que le **transaction_sequence_num**, ou **first_snapshot_sequence_num** colonnes dans le [sys.dm_tran_active_snapshot_database_transactions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) vue de gestion dynamique contient une valeur de 15. Si le **transaction_sequence_num**, ou **first_snapshot_sequence_num** colonnes dans la vue contient un nombre qui est inférieur à la dernière transaction effectuée par une opération de réduction (109), l’opération de réduction attendra que ces transactions soient terminées.
  
Pour résoudre le problème, vous pouvez effectuer l’une des tâches suivantes :
-   Achevez la transaction qui bloque l'opération de réduction.  
-   Achevez l'opération de réduction. Tout travail achevé sera conservé.  
-   Laissez simplement l'opération de réduction attendre que la transaction bloquante s'achève.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance au rôle de serveur fixe **sysadmin** ou au rôle de base de données fixe **db_owner** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-shrinking-a-database-and-specifying-a-percentage-of-free-space"></a>A. Réduction de la taille d'une base de données et spécification d'un pourcentage d'espace libre  
 L'exemple suivant diminue la taille des fichiers de données et journaux de la base de données utilisateur `UserDB` pour obtenir 10 % d'espace libre dans la base de données.  
  
```sql  
DBCC SHRINKDATABASE (UserDB, 10);  
GO  
```  
  
### <a name="b-truncating-a-database"></a>B. Troncation d'une base de données  
 L'exemple suivant réduit la taille des fichiers de données et des fichiers journaux de l'exemple de base de données `AdventureWorks` jusqu'à la dernière extension allouée.  
  
```sql  
DBCC SHRINKDATABASE (AdventureWorks2012, TRUNCATEONLY);  
```  
  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
[Réduire une base de données](../../relational-databases/databases/shrink-a-database.md)
  
  

