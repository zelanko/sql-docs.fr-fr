---
title: Créer une transaction distribuée Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f21ea9b7146b2907a09688f5189d6d9ae4f3f26a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303692"
---
# <a name="create-a-distributed-transaction"></a>Créer une transaction distribuée

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->


Une transaction distribuée peut être créée pour différents systèmes Microsoft SQL de différentes manières.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>Le conducteur de l’ODBC appelle le MSDTC pour SQL Server sur place

Le Coordinateur microsoft des transactions distribuées (MSDTC) permet aux applications [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]d’étendre ou de _distribuer_ une transaction dans deux cas ou plus de . La transaction distribuée fonctionne même lorsque les deux instances sont hébergées sur des ordinateurs distincts.

MSDTC est installé pour Microsoft SQL Server sur place, mais n’est pas disponible pour le service cloud Azure SQL Database de Microsoft.

MSDTC est appelé par le pilote SQL Server Native Client pour la connectivité open Database (ODBC), lorsque votre programme CMD gère une transaction distribuée. Le pilote native Client ODBC dispose d’un gestionnaire de transaction conforme à la norme XA de traitement des transactions distribuées (DTP) du groupe ouvert (DTP). Cette conformité est requise par MSDTC. En règle générale, toutes les commandes de gestion des transactions sont envoyées par l’intermédiaire de ce pilote ODBC de client autochtone. La séquence est la suivante :

1. Votre application ODBC native CMD démarre une transaction en appelant [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), avec le mode autocommit désactivé.

2. L’application met à jour certaines données sur SQL Server X sur l’ordinateur A.

3. L’application met à jour certaines données sur SQL Server Y sur l’ordinateur B.
    - Si une mise à jour sur SQL Server Y échoue, toutes les mises à jour non engagées sur les deux instances SQL Server sont annulées.

4. Enfin, l’application met fin à la transaction en appelant [SQLEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md), avec l’option SQL_COMMIT ou SQL_ROLLBACK.

_(1)_ MSDTC peut être invoqué sans ODBC. Dans un tel cas, MSDTC devient le gestionnaire de transaction, et l’application n’utilise plus **SQLEndTran**.

### <a name="only-one-distributed-transaction"></a>Une seule transaction distribuée

Supposons que votre application ODBC de client autochtone de CMD soit enrôlée dans le fait d’une transaction distribuée. Ensuite, l’application s’enrôle dans une deuxième transaction distribuée. Dans ce cas, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC quitte la transaction distribuée originale et s’enrôle dans la nouvelle transaction distribuée.

Pour plus d’informations, consultez [la référence du programmeur DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>Alternative CMD pour SQL Database dans le cloud

MSDTC n’est pris en charge ni pour Azure SQL Database ni Azure SQL Data Warehouse.

Cependant, une transaction distribuée peut être créée pour SQL Database en ayant votre programme C’emploi de la classe .NET [System.Transactions.TransactionScope](/dotnet/api/system.transactions.transactionscope).

### <a name="other-programming-languages"></a>Autres langages de programmation

Les autres langages de programmation suivants pourraient ne pas fournir de soutien pour les transactions distribuées avec le service sqL Database :

- Native CMD qui utilisent des chauffeurs ODBC
- Serveur lié à l’aide de Transact-SQL
- Pilotes JDBC

## <a name="see-also"></a>Voir aussi

[Exécution de transactions (ODBC)](performing-transactions-in-odbc.md)
