---
title: ALTER DATABASE (Parallel Data Warehouse) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5751656b-7aae-4152-a314-4c631bea4fc4
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 74b47bec1033728d47e5fe577af29c6d43e9af65
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-parallel-data-warehouse"></a>MODIFIER la base de données (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Modifie les options de taille maximale de la base de données pour les tables répliquées, tables distribuées et le journal des transactions dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Cette instruction permet de gérer les allocations d’espace disque pour une base de données augmente ou diminue la taille.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Parallel Data Warehouse  
ALTER DATABASE database_name    
    SET ( <set_database_options>   | <db_encryption_option> )  
[;]  
  
<set_database_options> ::=   
{  
    AUTOGROW = { ON | OFF }  
    | REPLICATED_SIZE = size [GB]  
    | DISTRIBUTED_SIZE = size [GB]  
    | LOG_SIZE = size [GB]  
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Le nom de la base de données à modifier. Pour afficher une liste des bases de données sur le matériel, utilisez [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
 CROISSANCE AUTOMATIQUE = {ON | {OFF}  
 L’option de croissance automatique des mises à jour. Lors de la croissance automatique est activée, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] augmente automatiquement l’espace alloué pour les tables répliquées, tables distribuées et le journal des transactions que nécessaire pour prendre en charge la croissance des besoins de stockage. Lors de la croissance automatique est désactivée, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] retourne une erreur si des tables, répliquées distribuées tables, ou le journal des transactions dépasse le paramètre de taille maximale.  
  
 REPLICATED_SIZE = *taille* [Go]  
 Spécifie les nouveau gigaoctets maximales par nœud de calcul pour le stockage de toutes les tables répliquées dans la base de données qui est modifiée. Si vous envisagez d’espace de stockage de matériel, vous devez multiplier REPLICATED_SIZE par le nombre de nœuds de calcul dans l’appliance.  
  
 DISTRIBUTED_SIZE = *taille* [Go]  
 Spécifie les nouveau gigaoctets maximales par base de données pour le stockage de toutes les tables distribuées dans la base de données qui est modifiée. La taille est répartie sur tous les nœuds de calcul dans l’appliance.  
  
 LOG_SIZE = *taille* [Go]  
 Spécifie les nouveau gigaoctets maximales par base de données pour le stockage de tous les journaux des transactions dans la base de données qui est modifiée. La taille est répartie sur tous les nœuds de calcul dans l’appliance.  
  
 CHIFFREMENT {ON | {OFF}  
 Spécifie si la base de données doit être chiffrée (ON) ou non chiffrée (OFF). Le chiffrement peut être configuré que pour [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] lorsque [sp_pdw_database_encryption pour](http://msdn.microsoft.com/5011bb7b-1793-4b2b-bd9c-d4a8c8626b6e) a été défini sur **1**. Une clé de chiffrement de base de données doit être créée avant de pouvoir configurer le chiffrement transparent des données. Pour plus d’informations sur le chiffrement de base de données, consultez [Transparent Data Encryption &#40; Chiffrement transparent des données &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="permissions"></a>Permissions  
 Requiert l’autorisation ALTER sur la base de données.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Les valeurs de REPLICATED_SIZE, DISTRIBUTED_SIZE et LOG_SIZE peuvent être supérieur à, égal à, inférieur ou les valeurs actuelles de la base de données.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Croissance et les opérations de compactage sont approximatives. Les tailles réelles qui en résulte peuvent varier selon les paramètres de taille.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]n’effectue pas l’instruction ALTER DATABASE comme une opération atomique. Si l’instruction est abandonnée pendant l’exécution, les modifications qui ont eu lieu restera.  
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
 Acquiert un verrou partagé sur l’objet de base de données. Vous ne pouvez pas modifier une base de données est en cours d’utilisation par un autre utilisateur pour la lecture ou l’écriture. Cela inclut les sessions qui ont émis un [utilisez](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15) instruction sur la base de données.  
  
## <a name="performance"></a>Performance  
 Réduction d’une base de données peut prendre beaucoup de temps et des ressources système, selon la taille des données réelles dans la base de données et la quantité de fragmentation sur le disque. Par exemple, la réduction d’une base de données peut prendre plusieurs heures ou plus.  
  
## <a name="determining-encryption-progress"></a>Déterminer la progression du chiffrement  
 Pour déterminer la progression du chiffrement transparent des données de base de données sous forme de pourcentage, utilisez la requête suivante :  
  
```  
WITH  
database_dek AS (  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id,  
        dek.encryption_state, dek.percent_complete,  
        dek.key_algorithm, dek.key_length, dek.encryptor_thumbprint,  
        type  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
    INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
        ON dek.database_id = node_db_map.database_id   
        AND dek.pdw_node_id = node_db_map.pdw_node_id  
    LEFT JOIN sys.pdw_database_mappings AS db_map  
        ON node_db_map .physical_name = db_map.physical_name  
    INNER JOIN sys.dm_pdw_nodes nodes  
        ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
),  
dek_percent_complete AS (  
    SELECT database_dek.database_id, AVG(database_dek.percent_complete) AS percent_complete  
    FROM database_dek  
    WHERE type = 'COMPUTE'  
    GROUP BY database_dek.database_id  
)  
SELECT DB_NAME( database_dek.database_id ) AS name,  
    database_dek.database_id,  
    ISNULL(  
       (SELECT TOP 1 dek_encryption_state.encryption_state  
        FROM database_dek AS dek_encryption_state  
        WHERE dek_encryption_state.database_id = database_dek.database_id  
        ORDER BY (CASE encryption_state  
            WHEN 3 THEN -1  
            ELSE encryption_state  
            END) DESC), 0)  
        AS encryption_state,  
dek_percent_complete.percent_complete,  
database_dek.key_algorithm, database_dek.key_length, database_dek.encryptor_thumbprint  
FROM database_dek  
INNER JOIN dek_percent_complete   
    ON dek_percent_complete.database_id = database_dek.database_id  
WHERE type = 'CONTROL';  
```  
  
 Pour obtenir un exemple complet qui montre toutes les étapes de l’implémentation de chiffrement transparent des données, consultez [Transparent Data Encryption &#40; Chiffrement transparent des données &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Exemples :[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. Modification du paramètre de croissance automatique  
 Activée croissance automatique pour la base de données `CustomerSales`.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>B. Modifier le stockage maximal pour les tables répliquées  
 L’exemple suivant définit la limite de stockage de table répliqué à 1 Go pour la base de données `CustomerSales`. Il s’agit de la limite de stockage par nœud de calcul.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>C. Modifier le stockage maximal pour les tables distribuées  
 L’exemple suivant définit la limite de stockage de table distribuée à 1 000 Go (un téraoctet) pour la base de données `CustomerSales`. Il s’agit de la limite de stockage combiné pour l’application pour tous les nœuds de calcul, pas la limite de stockage par nœud de calcul.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>D. Modifier le stockage maximal pour le journal des transactions  
 L’exemple suivant met à jour la base de données `CustomerSales` pour avoir un maximum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] taille de journal de transactions de 10 Go pour l’application.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une base de données &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/create-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  

