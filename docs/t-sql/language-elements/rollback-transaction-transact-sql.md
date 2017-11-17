---
title: ROLLBACK TRANSACTION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROLLBACK TRANSACTION
- ROLLBACK
- ROLLBACK_TSQL
- ROLLBACK_TRANSACTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transaction rollbacks [SQL Server]
- ROLLBACK TRANSACTION statement
- erasing data modifications [SQL Server]
- rolling back transactions, ROLLBACK TRANSACTION
- roll back transactions [SQL Server]
- savepoints [SQL Server]
ms.assetid: 6882c5bc-ff74-476a-984b-164aeb036c66
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: 7a7cf37490b1dab17a061104ab14b5d11d26632d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/14/2017

---
# <a name="rollback-transaction-transact-sql"></a>ROLLBACK TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Annule une transaction implicite ou explicite jusqu'au début de la transaction ou jusqu'au dernier point d'enregistrement à l'intérieur de la transaction. Vous pouvez utiliser ROLLBACK TRANSACTION pour effacer toutes les modifications de données effectuées depuis le début de la transaction ou à partir d'un point d'enregistrement. Elle libère également les ressources bloquées par la transaction.  
  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ROLLBACK { TRAN | TRANSACTION }   
     [ transaction_name | @tran_name_variable  
     | savepoint_name | @savepoint_variable ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *argument*  
 Nom attribué à la transaction dans BEGIN TRANSACTION *argument* doit être conforme aux règles des identificateurs, mais seuls les 32 premiers caractères du nom de transaction sont utilisés. En cas d’imbrication des transactions, *argument* doit être le nom de l’instruction BEGIN TRANSACTION la plus extérieure. *argument* est toujours la casse, même lorsque l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne respecte pas la casse.  
  
 **@***variable_nom_transaction*  
 Nom d'une variable définie par l'utilisateur et contenant un nom de transaction valide. La variable doit être déclarée avec un **char**, **varchar**, **nchar**, ou **nvarchar** type de données.  
  
 *savepoint_name*  
 Est *savepoint_name* à partir d’une instruction SAVE TRANSACTION. *savepoint_name* doit être conforme aux règles des identificateurs. Utilisez *savepoint_name* quand une opération d’annulation conditionnelle doit affecter qu’une partie de la transaction.  
  
 **@***savepoint_variable*  
 Nom d'une variable définie par l'utilisateur et contenant un nom de point d'enregistrement valide. La variable doit être déclarée avec un **char**, **varchar**, **nchar**, ou **nvarchar** type de données.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Une instruction ROLLBACK TRANSACTION n'envoie aucun message à l'utilisateur. Si des avertissements sont nécessaires dans les procédures stockées ou les déclencheurs, utilisez les instructions RAISERROR ou PRINT. L'instruction RAISERROR est la mieux adaptée à l'indication des erreurs.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 ROLLBACK TRANSACTION sans un *savepoint_name* ou *argument* restaure le début de la transaction. En cas d'imbrication des transactions, cette même instruction annule toutes les transactions internes jusqu'à l'instruction BEGIN TRANSACTION la plus extérieure. Dans les deux cas, ROLLBACK TRANSACTION le @@TRANCOUNT fonction système à 0. ROLLBACK TRANSACTION *savepoint_name* ne décrémente pas@TRANCOUNT.  
  
 ROLLBACK TRANSACTION ne peut pas référencer un *savepoint_name* dans les transactions distribuées démarrées explicitement avec BEGIN DISTRIBUTED TRANSACTION, soit découlant d’une transaction locale.  
  
 Une transaction ne peut pas être annulée après l'exécution d'une instruction COMMIT TRANSACTION, sauf lorsque l'instruction COMMIT TRANSACTION est associée à une transaction imbriquée qui est contenue dans la transaction restaurée. Dans ce cas, la transaction imbriquée est est restaurée, même si vous avez émis une instruction COMMIT TRANSACTION pour celle-ci.  
  
 Dans une transaction, les noms de point d'enregistrement dupliqués sont autorisés. Toutefois, une instruction ROLLBACK TRANSACTION contenant un nom de point d'enregistrement en double n'effectue l'annulation que jusqu'à l'instruction SAVE TRANSACTION la plus récente utilisant ce nom de point d'enregistrement.  
  
## <a name="interoperability"></a>Interopérabilité  
 Dans les procédures stockées, les instructions ROLLBACK TRANSACTION sans un *savepoint_name* ou *argument* restaurer toutes les instructions de la première instruction BEGIN transaction. Une instruction ROLLBACK TRANSACTION dans une procédure stockée qui provoque @@TRANCOUNT pour avoir une valeur différente lorsque la procédure stockée se termine et celui du @@TRANCOUNT valeur lors de l’appel de la procédure stockée génère un message d’information. Ce message n'affecte pas la suite du traitement.  
  
 L'exécution d'une instruction ROLLBACK TRANSACTION dans un déclencheur a les conséquences suivantes :  
  
-   toutes les modifications de données effectuées jusque là dans la transaction en cours sont annulées, y compris celles effectuées par le déclencheur ;  
  
-   le déclencheur termine l'exécution des instructions qui suivent l'instruction ROLLBACK. Si l'une de ces instructions modifie les données, les modifications ne sont pas annulées. Aucun déclencheur imbriqué ne peut être activé par l'exécution de ces instructions ;  
  
-   aucune instruction du traitement suivant celle qui a activé le déclencheur n'est exécutée.  
  
@@TRANCOUNT est incrémenté d’un à l’entrée d’un déclencheur, même en mode autocommit. (Le système traite un déclencheur comme une transaction imbriquée implicite).  
  
Les instructions ROLLBACK TRANSACTION contenues dans des procédures stockées n'affectent pas les instructions suivantes dans le traitement qui a appelé la procédure ; les instructions suivantes du traitement sont exécutées. Les instructions ROLLBACK TRANSACTION figurant dans des déclencheurs terminent le traitement contenant l'instruction qui a activé le déclencheur ; les instructions suivantes du traitement ne sont pas exécutées.  
  
Les effets d'une instruction ROLLBACK sur les curseurs sont définis par les trois règles suivantes :  
  
1.  avec CURSOR_CLOSE_ON_COMMIT à ON, ROLLBACK ferme tous les curseurs ouverts, sans les désallouer ;  
  
2.  avec CURSOR_CLOSE_ON_COMMIT à OFF, ROLLBACK n'affecte ni les curseurs synchrones STATIC ou INSENSITIVE ouverts, ni les curseurs STATIC asynchrones entièrement remplis. Quel que soit leur type, les curseurs ouverts sont fermés mais pas désalloués ;  
  
3.  une erreur qui termine un traitement et génère une annulation interne provoque la désallocation de tous les curseurs qui étaient déclarés dans le traitement contenant l'instruction erronée. Tous les curseurs sont désalloués, quel que soit leur type ou le paramétrage de CURSOR_CLOSE_ON_COMMIT. Cela inclut les curseurs déclarés dans les procédures stockées appelées par le traitement qui a provoqué l'erreur. Les curseurs déclarés dans un traitement précédant le traitement erroné sont soumis aux règles 1 et 2. Un blocage est un exemple de ce type d'erreur. Une instruction ROLLBACK exécutée dans un déclencheur génère aussi automatiquement ce type d'erreur.  
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
 Une instruction ROLLBACK TRANSACTION spécifiant un *savepoint_name* libère tous les verrous acquis au-delà du point d’enregistrement, à l’exception des promotions et des conversions. Ces verrous ne sont pas libérés et ne sont pas reconvertis dans leur ancien mode de verrouillage.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre l'effet de la restauration d'une transaction nommée. Après avoir créé une table, les instructions suivantes démarre une transaction nommée, insérer deux lignes, puis restaurer la transaction nommée dans la variable @TransactionName. Une autre instruction en dehors de la transaction nommée insère deux lignes. La requête retourne les résultats de ces instructions.   
  
```sql    
USE tempdb;  
GO  
CREATE TABLE ValueTable ([value] int);  
GO  
  
DECLARE @TransactionName varchar(20) = 'Transaction1';  
  
BEGIN TRAN @TransactionName  
       INSERT INTO ValueTable VALUES(1), (2);  
ROLLBACK TRAN @TransactionName;  
  
INSERT INTO ValueTable VALUES(3),(4);  
  
SELECT [value] FROM ValueTable;  
  
DROP TABLE ValueTable;  
```  
[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]  
```  
value  
-----   
3    
4  
```  
  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [VALIDER le travail &#40; Transact-SQL &#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [TRAVAIL de restauration &#40; Transact-SQL &#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  

