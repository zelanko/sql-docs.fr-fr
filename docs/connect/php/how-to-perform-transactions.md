---
title: 'Procédure : effectuer des transactions'
description: Cette rubrique explique et montre comment effectuer des transactions lors de l’utilisation des Pilotes Microsoft pour PHP pour SQL Server
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transaction support
ms.assetid: f4643b85-f929-4919-8951-23394bc5bfa7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 13eae20e5a8e51a7a46473ef62e98c03c195e382
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726823"
---
# <a name="how-to-perform-transactions"></a>Procédure : Effectuer des transactions
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Le pilote SQLSRV de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] propose trois fonctions pour effectuer des transactions :  
  
-   [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md)  
  
-   [sqlsrv_commit](../../connect/php/sqlsrv-commit.md)  
  
-   [sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md)  
  
Le pilote PDO_SQLSRV propose trois méthodes pour effectuer des transactions :  
  
-   [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md)  
  
-   [PDO::commit](../../connect/php/pdo-commit.md)  
  
-   [PDO::Rollback](../../connect/php/pdo-rollback.md)  
  
Consultez [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) pour obtenir un exemple.  
  
Le reste de cette rubrique explique et montre comment utiliser le pilote SQLSRV pour effectuer des transactions.  
  
## <a name="remarks"></a>Notes  
Les étapes d’exécution d’une transaction peuvent se résumer comme suit :  
  
1.  Commencez la transaction avec **sqlsrv_begin_transaction**.  
  
2.  Vérifiez si chaque requête incluse dans la transaction aboutit ou échoue.  
  
3.  Si nécessaire, validez la transaction avec **sqlsrv_commit**. Sinon, restaurez la transaction avec **sqlsrv_rollback**. Après avoir appelé **sqlsrv_commit** ou **sqlsrv_rollback**, le pilote repasse en mode de validation automatique.  
  
    Par défaut, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] est en mode de validation automatique. Cela signifie que toutes les requêtes sont validées automatiquement en cas de réussite, sauf si elles ont été désignées comme faisant partie d’une transaction explicite à l’aide de **sqlsrv_begin_transaction**.  
  
    Si une transaction explicite n’est pas validée avec **sqlsrv_commit**, elle est restaurée à la fermeture de la connexion ou à l’arrêt du script.  
  
    N’utilisez pas Transact-SQL incorporé pour effectuer des transactions. Par exemple, n’exécutez pas une instruction avec « BEGIN TRANSACTION » en tant que requête Transact-SQL pour commencer une transaction. Le comportement transactionnel attendu ne peut pas être garanti quand vous utilisez Transact-SQL incorporé pour effectuer des transactions.  
  
    Les fonctions **sqlsrv** répertoriées précédemment doivent être utilisées pour effectuer des transactions.  
  
## <a name="example"></a> Exemple  
  
### <a name="description"></a>Description  
L’exemple suivant exécute plusieurs requêtes dans le cadre d’une transaction. Si toutes les requêtes réussissent, la transaction est validée. Si l’une des requêtes échoue, la transaction est restaurée.  
  
L’exemple vise à supprimer une commande client de la table *Sales.SalesOrderDetail* et à ajuster le niveau de stock de chaque produit figurant dans cette commande dans la table *Product.ProductInventory* . Ces requêtes sont incluses dans une transaction, car elles doivent toutes réussir pour que la base de données reflète avec exactitude l’état des commandes et la disponibilité des produits.  
  
La première requête de l’exemple récupère les ID de produit et les quantités correspondant à un ID de commande client spécifié. Cette requête ne fait pas partie de la transaction. En revanche, le script se termine si cette requête échoue, car les ID de produit et les quantités sont requises pour exécuter les requêtes qui font partie de la transaction ultérieure.  
  
Les requêtes ultérieures (suppression de la commande client et mise à jour des quantités de stock des produits) font partie de la transaction.  
  
L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
### <a name="code"></a>Code  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Begin transaction. */  
if( sqlsrv_begin_transaction($conn) === false )   
{   
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set the Order ID.  */  
$orderId = 43667;  
  
/* Execute operations that are part of the transaction. Commit on  
success, roll back on failure. */  
if (perform_trans_ops($conn, $orderId))  
{  
     //If commit fails, roll back the transaction.  
     if(sqlsrv_commit($conn))  
     {  
         echo "Transaction committed.\n";  
     }  
     else  
     {  
         echo "Commit failed - rolling back.\n";  
         sqlsrv_rollback($conn);  
     }  
}  
else  
{  
     "Error in transaction operation - rolling back.\n";  
     sqlsrv_rollback($conn);  
}  
  
/*Free connection resources*/  
sqlsrv_close( $conn);  
  
/*----------------  FUNCTION: perform_trans_ops  -----------------*/  
function perform_trans_ops($conn, $orderId)  
{  
    /* Define query to update inventory based on sales order info. */  
    $tsql1 = "UPDATE Production.ProductInventory   
              SET Quantity = Quantity + s.OrderQty   
              FROM Production.ProductInventory p   
              JOIN Sales.SalesOrderDetail s   
              ON s.ProductID = p.ProductID   
              WHERE s.SalesOrderID = ?";  
  
    /* Define the parameters array. */  
    $params = array($orderId);  
  
    /* Execute the UPDATE statement. Return false on failure. */  
    if( sqlsrv_query( $conn, $tsql1, $params) === false ) return false;  
  
    /* Delete the sales order. Return false on failure */  
    $tsql2 = "DELETE FROM Sales.SalesOrderDetail   
              WHERE SalesOrderID = ?";  
    if(sqlsrv_query( $conn, $tsql2, $params) === false ) return false;  
  
    /* Return true because all operations were successful. */  
    return true;  
}  
?>  
```  
  
### <a name="comments"></a>Commentaires  
Pour mieux mettre l’accent sur le comportement de la transaction, aucune recommandation en matière de gestion des erreurs n’est donnée dans l’exemple précédent. Pour une application de production, nous vous recommandons de vérifier s’il existe des erreurs et de les gérer en conséquence dans tout appel à une fonction **sqlsrv**.
  
## <a name="see-also"></a>Voir aussi  
[Mise à jour des données &#40;pilotes Microsoft SQL Server pour PHP&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

[Transactions (moteur de base de données)](/previous-versions/sql/sql-server-2008-r2/ms190612(v=sql.105))

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
