---
title: DBCC SHRINKDATABASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: 8ebabe4403d65447bcf7ab4d88f36b9fd9715843
ms.sourcegitcommit: 2ab79765e51913f1df6410f0cd56bf2a13221f37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2019
ms.locfileid: "56956020"
---
# <a name="dbcc-shrinkdatabase-transact-sql"></a>DBCC SHRINKDATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
_database\_name_ | _database\_id_ | 0  
Nom ou ID de la base de données à réduire. 0 indique que la base de données active est utilisée.  
  
_target\_percent_  
Pourcentage d'espace que vous voulez laisser disponible dans le fichier de la base de données après sa réduction.  
  
NOTRUNCATE  
Déplace les pages affectées de la fin du fichier vers les pages non affectées du début du fichier. Cette action compacte les données dans le fichier. _target\_percent_ est facultatif. Azure SQL Data Warehouse ne prend pas en charge cette option. 
  
L’espace libre à la fin du fichier n’est pas restitué au système d’exploitation et la taille physique du fichier ne change pas. Ainsi, la base de données ne paraît pas être réduite quand vous spécifiez l’option NOTRUNCATE.  
  
NOTRUNCATE n'est applicable qu'aux fichiers de données. NOTRUNCATE n’affecte pas le fichier journal.  
  
TRUNCATEONLY  
Libère tout l’espace libre à la fin du fichier pour le système d’exploitation. N’effectue aucun déplacement de page au sein du fichier. Le fichier de données est réduit seulement jusqu’à la dernière extension affectée. _target\_percent_ est ignoré s’il est spécifié avec TRUNCATEONLY. Azure SQL Data Warehouse ne prend pas en charge cette option.
  
TRUNCATEONLY affecte le fichier journal. Pour tronquer uniquement le fichier de données, utilisez DBCC SHRINKFILE.  
  
WITH NO_INFOMSGS  
Supprime tous les messages d'information dont les niveaux de gravité sont compris entre 0 et 10.  
  
## <a name="result-sets"></a>Jeux de résultats  
Le tableau suivant décrit les colonnes du jeu de résultats.
  
|Nom de colonne|Description|  
|-----------------|-----------------|  
|**DbId**|Numéro d'identification de base de données du fichier que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] tente de réduire.|  
|**FileId**|Numéro d'identification du fichier que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] tente de réduire.|  
|**CurrentSize**|Nombre de pages de 8 Ko que le fichier occupe actuellement.|  
|**MinimumSize**|Nombre de pages de 8 Ko que le fichier pourrait occuper au minimum. Cette valeur correspond à la taille minimale ou à la taille de création d’un fichier.|  
|**UsedPages**|Nombre de pages de 8 Ko que le fichier utilise actuellement.|  
|**EstimatedPages**|Nombre de pages de 8 Ko estimé par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] auquel la taille du fichier peut être ramenée.|  
  
>[!NOTE]
> Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n'affiche pas de ligne pour les fichiers qui ne sont pas réduits.  
  
## <a name="remarks"></a>Notes   

>[!NOTE]
> Actuellement, Azure SQL Data Warehouse ne prend pas en charge DBCC SHRINKDATABASE. L’exécution de cette commande n’est pas recommandée, car c’est une opération qui consomme beaucoup d’E/S et qui peut déconnecter votre entrepôt de données. Par ailleurs, l’exécution de cette commande entraîne de coûteuses implications sur vos instantanés d’entrepôt de données. 

Pour réduire tous les fichiers de données et fichiers journaux d'une base de données particulière, exécutez la commande DBCC SHRINKDATABASE. Pour réduire un fichier de données ou un fichier journal d'une base de données particulière, exécutez la commande [DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md).
  
Pour afficher la quantité d'espace actuellement libre (non allouée) dans la base de données, exécutez [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md).
  
Les opérations DBCC SHRINKDATABASE peuvent être arrêtées à n’importe quel stade du processus, chaque travail terminé étant conservé.
  
La base de données ne peut pas être réduite à une taille inférieure à la taille minimale configurée de la base de données. Vous indiquez la taille minimale lors de la création de la base de données. Il peut s’agir aussi de la dernière taille explicitement définie à l’aide d’une opération de changement de taille de fichier. Des opérations comme DBCC SHRINKFILE ou ALTER DATABASE sont des exemples d’opérations de changement de taille de fichier. 

Supposons qu’une base de données est créée avec une taille de 10 Mo. Elle atteint ensuite une taille de 100 Mo. La base de données ne peut pas être réduite à moins de 10 Mo, même si toutes les données de la base de données sont supprimées.
  
Spécifiez l’option NOTRUNCATE ou l’option TRUNCATEONLY quand vous exécutez DBCC SHRINKDATABASE. Sinon, cela revient à exécuter une opération DBCC SHRINKDATABASE avec NOTRUNCATE suivie d’une opération DBCC SHRINKDATABASE avec TRUNCATEONLY.
  
Il n’est pas nécessaire que la base de données réduite soit en mode mono-utilisateur. D’autres utilisateurs peuvent travailler dans la base de données quand elle est réduite, notamment les bases de données système.
  
Vous ne pouvez pas réduire la taille d’une base de données en cours de sauvegarde. Inversement, vous ne pouvez pas sauvegarder une base de données alors qu’elle fait l’objet d’une opération de réduction.
  
## <a name="how-dbcc-shrinkdatabase-works"></a>Fonctionnement de DBCC SHRINKDATABASE  
DBCC SHRINKDATABASE réduit les fichiers de données, fichier par fichier, mais réduit les fichiers journaux comme si tous les fichiers journaux existaient dans un groupe de journaux contigus. Les fichiers sont toujours réduits à partir de la fin.
  
Supposons que vous disposez de deux fichiers journaux, d’un fichier de données et d’une base de données nommée **mydb**. La taille de chacun des fichiers est de 10 Mo et le fichier de données contient 6 Mo de données. Pour chaque fichier, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcule une taille cible, qui est la taille à laquelle le fichier doit être réduit. Quand DBCC SHRINKDATABASE est spécifié avec _target\_percent_, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcule la taille cible pour qu’elle corresponde à la quantité _target\_percent_ d’espace disponible dans le fichier après la réduction. 

Par exemple, si vous spécifiez un _target\_percent_ de 25 pour réduire **mydb**, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcule une taille cible de 8 Mo pour le fichier de données (6 Mo de données plus 2 Mo d’espace libre). Par conséquent, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] déplace toutes les données des 2 derniers Mo du fichier de données vers tout espace libre dans les 8 premiers Mo du fichier de données, puis réduit le fichier.
  
Supposons que le fichier de données de **mydb** contient 7 Mo de données. Si vous spécifiez un _target\_percent_ de 30, le fichier de données peut être réduit à 30 % d’espace libre. En revanche, si vous spécifiez un _target\_percent_ de 40, le fichier de données ne peut pas être réduit, car le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ne peut pas réduire un fichier à une taille inférieure à celle qu’occupent les données actuellement. 

Ce problème peut également être envisagé autrement : 40 % d’espace libre souhaité ajoutés à 70 % pour la taille du fichier de données (7 Mo sur 10 Mo) dépassent 100 %. Toute valeur _target\_size_ supérieure à 30 n’entraîne pas la réduction du fichier de données. En effet, la somme du pourcentage d’espace libre souhaité et du pourcentage actuel occupé par le fichier de données est supérieure à 100 %.
  
Dans le cas des fichiers journaux, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilise _target\_percent_ pour calculer la taille cible de l’ensemble du journal. _target\_percent_ correspond donc à la quantité d’espace libre dans le journal après l’opération de réduction. La taille cible pour le journal complet est alors convertie en taille cible pour chaque fichier journal.
  
DBCC SHRINKDATABASE essaie immédiatement de réduire chaque fichier journal physique à sa taille cible. Supposons qu’aucune partie du journal logique ne reste dans les journaux virtuels au-delà de la taille cible du fichier journal. Le fichier est alors tronqué avec succès et DBCC SHRINKDATABASE s’exécute sans émettre de messages. Toutefois, si une partie du journal logique reste dans les journaux virtuels au-delà de la taille cible, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] libère autant d’espace que possible, puis envoie un message d’information. Le message décrit les actions à effectuer pour déplacer le journal logique à partir des journaux virtuels à la fin du fichier. Une fois les actions exécutées, DBCC SHRINKDATABASE peut être utilisé pour libérer l’espace restant.
  
Un fichier journal ne peut être réduit que jusqu’à une limite virtuelle. C’est pourquoi il arrive qu’il ne soit pas possible de réduire un fichier journal à une taille inférieure à celle d’un fichier journal virtuel, même s’il n’est pas utilisé. La taille du fichier journal virtuel est choisie dynamiquement par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] au moment de la création ou de l'extension des fichiers journaux.
  
## <a name="best-practices"></a>Bonnes pratiques  
Prenez en compte les informations suivantes lorsque vous envisagez de réduire une base de données :
-   Une opération de réduction est plus efficace après une opération. Cette opération crée un espace inutilisé, par exemple une troncature ou une suppression de table.  
-   Un certain espace libre doit exister pour les opérations quotidiennes courantes pour la plupart des bases de données. Vous pouvez réduire plusieurs fois la taille d’une base de données et constater que la taille augmente de nouveau. Cette croissance indique que l’espace qui a été réduit est nécessaire pour les opérations courantes. Dans ce cas, la réduction de la taille de la base de données ne sert à rien.  
-   Une opération de réduction ne conserve pas l'état de fragmentation des index de la base de données ; en général, elle augmente la fragmentation dans une certaine mesure. Ce résultat représente une raison supplémentaire de ne pas réduire la taille de la base de données de manière répétitive.  
-   Sauf en cas de besoin précis, n’attribuez pas la valeur ON à l’option de base de données AUTO_SHRINK.  
  
## <a name="troubleshooting"></a>Dépannage  
Les opérations de réduction peuvent être bloquées par une transaction en cours d’exécution sous un [niveau d’isolation basé sur le contrôle de version de ligne](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md). Par exemple, si une opération de suppression de grande envergure sous un niveau d’isolation basé sur le contrôle de version de ligne se déroule parallèlement à une opération DBCC SHRINK DATABASE, l’opération de réduction attend la fin de l’opération de suppression pour réduire la taille des fichiers. Dans ce cas, les opérations DBCC SHRINKFILE et DBCC SHRINKDATABASE envoient un message d’information (5202 pour SHRINKDATABASE et 5203 pour SHRINKFILE). Ce message s’affiche dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] toutes les cinq minutes au cours de la première heure, puis toutes les heures. Par exemple, si le journal des erreurs contient le message d'erreur :  
  
```sql
DBCC SHRINKDATABASE for database ID 9 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
Cette erreur signifie que l’opération de réduction est bloquée par des transactions d’instantanés ayant des valeurs d’horodatage plus anciennes que 109. Cette transaction est la dernière transaction que l’opération de réduction a effectuée. Cela indique également que la colonne **transaction_sequence_num** ou **first_snapshot_sequence_num** dans la vue de gestion dynamique [sys.dm_tran_active_snapshot_database_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) contient une valeur de 15. La colonne **transaction_sequence_num** ou **first_snapshot_sequence_num** dans la vue peut contenir un numéro inférieur à la dernière transaction effectuée par une opération de réduction (109). Dans ce cas, l’opération de réduction attend que ces transactions soient terminées.
  
Pour résoudre ce problème, vous pouvez effectuer l'une des tâches suivantes :
-   Mettez fin à la transaction qui bloque l'opération de réduction.  
-   Mettez fin à l'opération de réduction. Tout travail achevé sera conservé.  
-   Laissez simplement l'opération de réduction attendre que la transaction bloquante s'achève.  
  
## <a name="permissions"></a>Permissions  
Nécessite l’appartenance au rôle de serveur fixe **sysadmin** ou au rôle de base de données fixe **db_owner** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-shrinking-a-database-and-specifying-a-percentage-of-free-space"></a>A. Réduction de la taille d'une base de données et spécification d'un pourcentage d'espace libre  
L’exemple suivant diminue la taille des fichiers de données et journaux de la base de données utilisateur `UserDB` pour obtenir 10 % d’espace libre dans la base de données.  
  
```sql  
DBCC SHRINKDATABASE (UserDB, 10);  
GO  
```  
  
### <a name="b-truncating-a-database"></a>b. Troncation d'une base de données  
L’exemple suivant réduit la taille des fichiers de données et des fichiers journaux de l’exemple de base de données `AdventureWorks` jusqu’à la dernière extension affectée.  
  
```sql  
DBCC SHRINKDATABASE (AdventureWorks2012, TRUNCATEONLY);  
```  
  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
[Réduire une base de données](../../relational-databases/databases/shrink-a-database.md)
  
  
