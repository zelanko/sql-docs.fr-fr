---
title: Transactions (SQL Data Warehouse) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 87e5e593-a121-4428-9d3c-3af876224e35
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8202a0de588bce3a36fc048e68c283b52db7e89d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="transactions-sql-data-warehouse"></a>Transactions (entrepôt de données SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Une transaction est un groupe d’une ou plusieurs instructions de base de données qui sont entièrement validée ou annulée. Chaque transaction est atomique, cohérentes, isolées et durables (ACID). Si la transaction réussit, toutes les instructions qu’il contient sont validées. Si la transaction échoue, qui est au moins une des instructions dans le groupe échoue, la totalité du groupe est restauré.  
  
 Le début et la fin des transactions varie selon le paramètre de validation automatique et les instructions BEGIN TRANSACTION, COMMIT et ROLLBACK. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]prend en charge les types de transactions suivants :  
  
-   *Transactions explicites* commencent par l’instruction BEGIN TRANSACTION et se terminent par l’instruction COMMIT ou ROLLBACK.  
  
-   *Transactions de validation automatique* lancer automatiquement au sein d’une session et ne commencent pas par l’instruction BEGIN TRANSACTION. Lors de la validation automatique est activé, chaque instruction s’exécute dans une transaction et aucune validation explicite ou restauration n’est nécessaire. Lorsque le paramètre de validation automatique est désactivée, une instruction COMMIT ou ROLLBACK est requis pour déterminer le résultat de la transaction. Dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], transactions validées automatiquement commencent immédiatement après une instruction COMMIT ou ROLLBACK, ou après une instruction SET AUTOCOMMIT OFF.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BEGIN TRANSACTION [;]  
COMMIT [ TRAN | TRANSACTION | WORK ] [;]  
ROLLBACK [ TRAN | TRANSACTION | WORK ] [;]  
SET AUTOCOMMIT { ON | OFF } [;]  
SET IMPLICIT_TRANSACTIONS { ON | OFF } [;]  
```  
  
## <a name="arguments"></a>Arguments  
 BEGIN TRANSACTION  
 Marque le point de départ d’une transaction explicite.  
  
 VALIDATION [TRAVAIL]  
 Marque la fin d’une transaction explicite ou validation automatique. Cette instruction provoque les modifications dans la transaction validée définitivement la base de données. L’instruction COMMIT est identique à COMMIT TRANSACTION, COMMIT TRAN et COMMIT WORK.  
  
 RESTAURATION [TRAVAIL]  
 Restaure une transaction au début de la transaction. Aucune modification de la transaction est validée dans la base de données. L’instruction ROLLBACK est identique à ROLLBACK WORK, ROLLBACK TRAN et ROLLBACK TRANSACTION.  
  
 ENSEMBLE AUTOCOMMIT { **ON** | {OFF}  
 Détermine la façon dont les transactions peuvent commencer et se terminer.  
  
 ON  
 Chaque instruction s’exécute sous sa propre transaction et aucune instruction COMMIT ou ROLLBACK explicite est nécessaire. Transactions explicites sont autorisées lors de la validation automatique est activée.  
  
 OFF  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]lance automatiquement une transaction lorsqu’une transaction n’est pas déjà en cours d’exécution. Toutes les instructions suivantes sont exécutées dans le cadre de la transaction et une validation ou restauration est nécessaire pour déterminer le résultat de la transaction. Dès qu’une transaction valide ou restaure sous ce mode de fonctionnement, le mode reste désactivée, et [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] lance une nouvelle transaction. Transactions explicites ne sont pas autorisées lors de la validation automatique est désactivée.  
  
 Si vous modifiez le paramètre de validation automatique dans une transaction active, le paramètre n’affecte pas la transaction en cours et ne prend pas effet tant que la transaction est terminée.  
  
 Si la validation automatique est activée, une autre instruction SET AUTOCOMMIT ON en cours d’exécution n’a aucun effet. De même, si la validation automatique est désactivée, exécutant une autre SET AUTOCOMMIT OFF n’a aucun effet.  
  
 SET IMPLICIT_TRANSACTIONS {ON | **OFF** }  
 Active/désactive les mêmes modes en tant que valeur de validation automatique. Si sa valeur est ON, SET IMPLICIT_TRANSACTIONS met la connexion en mode de transaction implicite. Lorsque OFF, il retourne la connexion en mode autocommit.  Pour plus d’informations, consultez [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41; ](../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Aucune autorisation spécifique est requise pour exécuter les instructions relatives aux transactions. Autorisations sont requises pour exécuter les instructions dans la transaction.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Si la validation ou restauration sont exécutées et il n’existe aucune transaction active, une erreur est générée.  
  
 Si une instruction BEGIN TRANSACTION est exécutée alors qu’une transaction est déjà en cours d’exécution, une erreur est générée. Cela peut se produire si une instruction BEGIN TRANSACTION se produit après une instruction BEGIN TRANSACTION réussie, ou lorsque la session est soumis à définir la validation automatique désactivé.  
  
 Si une erreur autre qu’une erreur d’exécution instruction empêche l’achèvement réussi d’une transaction explicite, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] automatiquement la transaction est restaurée et libère toutes les ressources détenues par la transaction. Par exemple, si la connexion du client réseau à une instance de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] est interrompue ou que le client se déconnecte de l’application, les transactions non validées pour la connexion sont annulées lors de la notification de l’instance de l’interruption.  
  
 Si une erreur de l’instruction d’exécution se produit dans un lot, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] comportement cohérent avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **XACT_ABORT** la valeur **ON** et toute la transaction est restaurée. Pour plus d’informations sur la **XACT_ABORT** , consultez [SET XACT_ABORT (Transact-SQL)](http://msdn.microsoft.com/library/ms188792.aspx).  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Une session peut exécuter seulement une seule transaction à un moment donné ; points d’enregistrement et les transactions imbriquées ne sont pas pris en charge.  
  
 Il incombe à le [!INCLUDE[DWsql](../../includes/dwsql-md.md)] programmeur pour émettre validation uniquement à un point lorsque toutes les données référencées par la transaction est logiquement correct.  
  
 Lorsqu’une session est arrêtée avant la fin d’une transaction, la transaction est restaurée.  
  
 Modes de transaction sont gérées au niveau de la session. Par exemple, si une session commence une transaction explicite ou définit le mode AUTOCOMMIT (OFF) ou définit IMPLICIT_TRANSACTIONS ON, il n’a aucun effet sur les modes de transaction des autres sessions.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Vous ne pouvez pas restaurer une transaction après qu’une instruction COMMIT est émise, car les modifications de données ont été apportées à une partie intégrante de la base de données.  
  
 Le [créer la base de données &#40; Entrepôt de données SQL Azure &#41; ](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) et [supprimer la base de données &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-database-transact-sql.md) commandes ne peut pas être utilisés à l’intérieur d’une transaction explicite.  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]n’a pas une mécanisme de partage de transaction. Cela implique qu’à un moment donné dans le temps, une seule session peut participer sur toutes les transactions dans le système.  
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]utilise le verrouillage pour garantir l’intégrité des transactions et de maintenir la cohérence des bases de données lorsque plusieurs utilisateurs accèdent aux données en même temps. Le verrouillage est utilisé par les transactions implicites et explicites. Chaque transaction demande des verrous de différents types de ressources, telles que des tables ou des bases de données dont dépend la transaction. Tous les [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] les verrous sont table ou ultérieure. Les verrous demandés empêchent les autres transactions d'apporter aux ressources des modifications susceptibles de nuire à la transaction. Chaque transaction libère ses verrous lorsqu’il a n’est plus une dépendance sur les ressources verrouillées ; transactions explicites conservent les verrous jusqu'à ce que la transaction se termine lorsqu’elle est validée ou restaurée.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-an-explicit-transaction"></a>A. À l’aide d’une transaction explicite  
  
```  
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```  
  
### <a name="b-rolling-back-a-transaction"></a>B. Restauration d’une transaction  
 L’exemple suivant montre l’effet de la restauration d’une transaction.  Dans cet exemple, l’instruction ROLLBACK annule l’instruction INSERT, mais la table existe toujours.  
  
```  
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  
```  
  
### <a name="c-setting-autocommit"></a>C. Paramètre de validation automatique  
 L’exemple suivant définit le paramètre de validation automatique `ON`.  
  
```  
SET AUTOCOMMIT ON;  
```  
  
 L’exemple suivant définit le paramètre de validation automatique `OFF`.  
  
```  
SET AUTOCOMMIT OFF;  
```  
  
### <a name="d-using-an-implicit-multi-statement-transaction"></a>D. À l’aide d’une transaction implicite de plusieurs instructions  
  
```  
SET AUTOCOMMIT OFF;  
CREATE TABLE ValueTable (id int);  
INSERT INTO ValueTable VALUES(1);  
INSERT INTO ValueTable VALUES(2);  
COMMIT;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  

