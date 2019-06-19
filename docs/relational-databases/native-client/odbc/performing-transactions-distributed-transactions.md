---
title: Créer des transactions distribuées | Microsoft Docs
ms.custom: ''
ms.date: 05/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ea6c4886a3c5397777b7a65afe96ab7e1b422bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65620542"
---
# <a name="create-a-distributed-transaction"></a>Créer une transaction distribuée

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

Une transaction distribuée peut être créée pour différents systèmes de Microsoft SQL de différentes façons.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>Pilote ODBC appelle le MSDTC pour SQL Server local

Microsoft Distributed Transaction Coordinator (MSDTC) permet aux applications d’étendre ou _distribuer_ une transaction sur deux ou plusieurs instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La transaction distribuée fonctionne même lorsque les deux instances sont hébergés sur des ordinateurs distincts.

MSDTC est installé pour Microsoft SQL Server local, mais il n’est pas disponible pour le service de cloud de Microsoft Azure SQL Database.

MSDTC est appelée par le pilote SQL Server Native Client pour Open Database Connectivity (ODBC), lorsque votre C++ programme gère une transaction distribuée. Le pilote ODBC Native Client possède un gestionnaire de transactions compatible avec l’Open groupe Distributed Transaction de traitement (DTP) XA standard. Cette conformité est requis par MSDTC. En règle générale, toutes les commandes de gestion de transaction sont envoyées via ce pilote ODBC Native Client. La séquence est comme suit :

1. Votre C++ application Native Client ODBC démarre une transaction en appelant [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), avec le mode de validation automatique désactivé.

2. L’application met à jour des données sur SQL Server X sur l’ordinateur A.

3. L’application met à jour des données sur SQL Server Y sur l’ordinateur B.
    - Si une mise à jour sur le serveur SQL Y échoue, toutes les mises à jour non validées sur les deux instances de SQL Server sont annulées.

4. Enfin, le l’application termine la transaction en appelant [SQLEndTran _(1)_ ](../../../relational-databases/native-client-odbc-api/sqlendtran.md), avec l’option le SQL_COMMIT ou SQL_ROLLBACK.

_(1)_  MSDTC peut être appelée sans ODBC. Dans ce cas, MSDTC devient le Gestionnaire de transactions, et l’application n’utilise plus **SQLEndTran**.

### <a name="only-one-distributed-transaction"></a>Seule une transaction distribuée

Supposons que votre C++ application Native Client ODBC est inscrite dans une transaction distribuée. Ensuite, l’application s’inscrit dans une deuxième transaction distribuée. Dans ce cas, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client quitte la transaction distribuée d’origine et s’inscrit dans la nouvelle transaction distribuée.

Pour plus d’informations, consultez [de référence du programmeur DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>C#solution de rechange pour la base de données SQL dans le cloud

MSDTC n’est pas pris en charge pour la base de données SQL Azure ou Azure SQL Data Warehouse.

Toutefois, une transaction distribuée peut être créée pour la base de données SQL en demandant à votre C# au programme d’utiliser la classe .NET [System.Transactions.TransactionScope](/dotnet/api/system.transactions.transactionscope).

### <a name="other-programming-languages"></a>Autres langages de programmation

Les éléments suivants autres langages de programmation peut ne pas fournissent une prise en charge pour les transactions distribuées avec le service de base de données SQL :

- Natif C++ qui utilisent des pilotes ODBC
- Serveur lié à l’aide de Transact-SQL
- Pilotes JDBC

## <a name="see-also"></a>Voir aussi

[Exécution de transactions (ODBC)](performing-transactions-in-odbc.md)
