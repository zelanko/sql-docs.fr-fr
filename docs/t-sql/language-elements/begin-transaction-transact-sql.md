---
title: "DÉBUT de la TRANSACTION (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BEGIN_TRANSACTION_TSQL
- TRANSACTION_TSQL
- TRANSACTION
- BEGIN TRANSACTION
- BEGIN TRAN
- BEGIN_TRAN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- transaction logs [SQL Server], BEGIN TRANSACTION statement
- marked transactions [SQL Server], BEGIN TRANSACTION statement
- BEGIN TRANSACTION statement
- local transactions [SQL Server]
- marking transactions [SQL Server]
- transactions [SQL Server], starting
- transaction names [SQL Server]
- starting point marked for transactions
- starting transactions
ms.assetid: c6258df4-11f1-416a-816b-54f98c11145e
caps.latest.revision: "56"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 968c0b5e8a35f6175ed739da716273e7231c6298
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="begin-transaction-transact-sql"></a>BEGIN TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Indique le début d'une transaction locale explicite. Transactions explicites commencent avec l’instruction BEGIN TRANSACTION et se terminent avec l’instruction COMMIT ou ROLLBACK.  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
--Applies to SQL Server and Azure SQL Database
 
BEGIN { TRAN | TRANSACTION }   
    [ { transaction_name | @tran_name_variable }  
      [ WITH MARK [ 'description' ] ]  
    ]  
[ ; ]  
```  
 
```  
--Applies to Azure SQL Data Warehouse and Parallel Data Warehouse
 
BEGIN { TRAN | TRANSACTION }   
[ ; ]  
```  

  
## <a name="arguments"></a>Arguments  
 *transaction_name*  
 **S’applique à :** SQL Server (à partir de 2008), base de données SQL Azure
 
 Nom attribué à la transaction. *argument* doit être conforme aux règles des identificateurs, mais les identificateurs de plus de 32 caractères ne sont pas autorisés. Utilisez les noms de transaction seulement sur la paire la plus extérieure des instructions BEGIN...COMMIT ou BEGIN...ROLLBACK imbriquées. *argument* est toujours la casse, même lorsque l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne respecte pas la casse.  
  
 @*tran_name_variable*  
 **S’applique à :** SQL Server (à partir de 2008), base de données SQL Azure
 
 Nom d'une variable définie par l'utilisateur et contenant un nom de transaction valide. La variable doit être déclarée avec un **char**, **varchar**, **nchar**, ou **nvarchar** type de données. Si plus de 32 caractères sont passés à la variable, seuls les 32 premiers caractères seront utilisés et les autres seront tronqués.  
  
 AVEC la marque ['*description*']  
**S’applique à :** SQL Server (à partir de 2008), base de données SQL Azure

Indique que la transaction est marquée dans le journal. *Description* est une chaîne qui décrit la marque. A *description* plus de 128 caractères est tronquée à 128 caractères avant d’être stockées dans la table msdb.dbo.logmarkhistory.  
  
 Si WITH MARK est utilisé, un nom de transaction doit être spécifié. WITH MARK permet de restaurer un journal de transactions par rapport à une marque nommée.  
  
## <a name="general-remarks"></a>Remarques d'ordre général
BEGIN TRANSACTION incrémente@TRANCOUNT par 1.
  
BEGIN TRANSACTION représente le point auquel les données référencées par une connexion sont logiquement et physiquement cohérentes. Si des erreurs sont détectées, toutes les modifications apportées aux données après l'exécution de l'instruction BEGIN TRANSACTION peuvent être annulées afin que les données reviennent à cet état connu de cohérence. Une transaction se poursuit jusqu'à ce qu'elle se termine sans erreur et que l'instruction COMMIT TRANSACTION soit émise pour que les modifications soient intégrées de façon permanente à la base de données ou bien jusqu'à ce que des erreurs soient rencontrées, auquel cas les modifications sont effacées à l'aide de l'instruction ROLLBACK TRANSACTION.  
  
L'instruction BEGIN TRANSACTION démarre une transaction locale pour la connexion qui a émis cette instruction. Selon les paramètres de niveau d'isolement définis pour la transaction en cours, de nombreuses ressources acquises pour la prise en charge des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] émises par la connexion sont verrouillées par la transaction jusqu'à ce que celle-ci se termine soit par un COMMIT TRANSACTION, soit par un ROLLBACK TRANSACTION. Les transactions suspendues pendant de longues périodes de temps peuvent empêcher les autres utilisateurs d'accéder à ces ressources verrouillées, et elles peuvent également empêcher la troncature du fichier journal.  
  
 Bien que BEGIN TRANSACTION démarre une transaction locale, celle-ci n'est pas enregistrée dans le journal des transactions avant que l'application n'effectue une action qui doit y être consignée, telle que l'exécution d'une instruction INSERT, UPDATE ou DELETE. Une application peut effectuer des actions telles que l'acquisition de verrous afin de protéger le niveau d'isolement d'une transaction des instructions SELECT, mais rien n'est enregistré dans le journal avant que l'application n'effectue une action de modification.  
  
 L'attribution d'un nom à plusieurs transactions d'une série de transactions imbriquées a peu d'effet sur la transaction. En effet, seul le premier nom de transaction (le plus à l'extérieur) est inscrit avec le système. Une annulation vers tout autre nom (autre que celui d'un point de sécurité valide) génère une erreur. Dans ce cas, aucune des instructions exécutées avant l'annulation n'est en fait annulée au moment où l'erreur se produit. Les instructions ne sont annulées que lorsque l'instruction extérieure est elle-même annulée.  
  
 La transaction locale lancée par l'instruction BEGIN TRANSACTION est promue au rang de transaction distribuée si les actions suivantes sont effectuées avant que cette transaction soit validée ou annulée :  
  
-   Exécution d'une instruction INSERT, DELETE ou UPDATE faisant référence à une table distante ou à un serveur lié. L’instruction INSERT, UPDATE ou DELETE échoue si le fournisseur OLE DB utilisé pour accéder au serveur lié ne prend pas en charge l’interface ITransactionJoin.  
  
-   Un appel à une procédure stockée distante est effectué quand l'option REMOTE_PROC_TRANSACTIONS a la valeur ON.  
  
 La copie locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devient le contrôleur de transaction et utilise [!INCLUDE[msCoName](../../includes/msconame-md.md)] DTC pour gérer la transaction distribuée.  
  
 Vous pouvez exécuter explicitement une transaction en tant que transaction distribuée en utilisant BEGIN DISTRIBUTED TRANSACTION. Pour plus d’informations, consultez [BEGIN DISTRIBUTED TRANSACTION &#40; Transact-SQL &#41; ](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md).  
  
 Si SET IMPLICIT_TRANSACTIONS a la valeur ON, une instruction BEGIN TRANSACTION crée deux transactions imbriquées. Pour plus d’informations, consultez [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)  
  
## <a name="marked-transactions"></a>Transactions marquées  
 L'option WITH MARK permet de placer le nom de la transaction dans le journal des transactions. Lors de la restauration d'une base de données à un état antérieur, la transaction marquée peut être utilisée à la place d'une date et d'une heure. Pour plus d’informations, consultez [utiliser les Transactions marquées pour récupérer des bases de données associées uniformément &#40; Mode de récupération complète &#41; ](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md) et [de restauration &#40; Transact-SQL &#41; ](../../t-sql/statements/restore-statements-transact-sql.md).  
  
 En outre, les marques du journal des transactions sont nécessaires pour récupérer un ensemble de bases de données connexes dans un état cohérent d'un point de vue logique. Une transaction distribuée permet de placer des marques dans les journaux de transactions des bases de données connexes. La récupération de l'ensemble de bases de données connexes jusqu'à ces marques aboutit à un ensemble de bases de données cohérent d'un point de vue transactionnel. Le placement de marques dans des bases de données connexes implique des procédures particulières.  
  
 La marque n'est placée dans le journal des transactions que si la base de données est mise à jour par la transaction marquée. Les transactions qui ne modifient pas de données ne sont pas marquées.  
  
 BEGIN TRAN *nouveau_nom* WITH MARK peut être imbriquée dans une transaction existante qui n’est pas marquée. Alors, *nouveau_nom* devient le nom de marque pour la transaction, malgré le nom de la transaction peut avoir déjà été fournie. Dans l'exemple suivant, `M2` est le nom de la marque.  
  
```  
BEGIN TRAN T1;  
UPDATE table1 ...;  
BEGIN TRAN M2 WITH MARK;  
UPDATE table2 ...;  
SELECT * from table1;  
COMMIT TRAN M2;  
UPDATE table3 ...;  
COMMIT TRAN T1;  
```  
  
 Lors de l'imbrication de transactions, si vous essayez de marquer une transaction déjà marquée, vous obtenez un message d'avertissement (et non pas d'erreur) :  
  
 « BEGIN TRAN T1 WITH MARK ...; »  
  
 « UPDATE table1 ...; »  
  
 « BEGIN TRAN M2 WITH MARK ...; »  
  
 « Serveur : Msg 3920, Niveau 16, État 1, Ligne 3 »  
  
 « L'option WITH MARK s'applique uniquement à la première instruction BEGIN TRAN WITH MARK. »  
  
 « L'option est ignorée. »  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-an-explicit-transaction"></a>A. À l’aide d’une transaction explicite
**S’applique à :** (à partir de 2008) de SQL Server, base de données SQL Azure, Azure SQL Data Warehouse, Parallel Data Warehouse

Cet exemple utilise AdventureWorks. 

```
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```

### <a name="b-rolling-back-a-transaction"></a>B. Restauration d’une transaction
**S’applique à :** (à partir de 2008) de SQL Server, base de données SQL Azure, Azure SQL Data Warehouse, Parallel Data Warehouse

L’exemple suivant montre l’effet de la restauration d’une transaction. Dans cet exemple, l’instruction ROLLBACK annule l’instruction INSERT, mais la table existe toujours.

```
 
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  

```

### <a name="c-naming-a-transaction"></a>C. Attribution d'un nom à une transaction 
**S’applique à :** SQL Server (à partir de 2008), base de données SQL Azure

L'exemple suivant montre comment nommer une transaction.  
  
```  
DECLARE @TranName VARCHAR(20);  
SELECT @TranName = 'MyTransaction';  
  
BEGIN TRANSACTION @TranName;  
USE AdventureWorks2012;  
DELETE FROM AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
  
COMMIT TRANSACTION @TranName;  
GO  
```  
  
### <a name="d-marking-a-transaction"></a>D. Marquage d'une transaction  
**S’applique à :** SQL Server (à partir de 2008), base de données SQL Azure

L'exemple suivant montre comment marquer une transaction. La transaction `CandidateDelete` est marquée.  
  
```  
BEGIN TRANSACTION CandidateDelete  
    WITH MARK N'Deleting a Job Candidate';  
GO  
USE AdventureWorks2012;  
GO  
DELETE FROM AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
GO  
COMMIT TRANSACTION CandidateDelete;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [COMMIT WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  
