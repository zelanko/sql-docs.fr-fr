---
title: Créer des transactions distribuées | Microsoft Docs
description: Les applications peuvent utiliser MSDTC pour étendre ou distribuer une transaction entre plusieurs instances de SQL Server. Une classe .NET peut également distribuer une transaction.
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
ms.openlocfilehash: e5ace381694dcc3afdbed36e35e48af147067b32
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92005965"
---
# <a name="create-a-distributed-transaction"></a>Créer une transaction distribuée

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->


Une transaction distribuée peut être créée pour différents systèmes Microsoft SQL de différentes manières.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>Le pilote ODBC appelle le MSDTC pour SQL Server localement

Le Distributed Transaction Coordinator Microsoft (MSDTC) permet aux applications d’étendre ou de _distribuer_ une transaction entre deux ou plusieurs instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . La transaction distribuée fonctionne même lorsque les deux instances sont hébergées sur des ordinateurs distincts.

MSDTC est installé pour Microsoft SQL Server localement, mais n’est pas disponible pour le service Cloud Azure SQL Database de Microsoft.

MSDTC est appelé par le pilote SQL Server Native Client pour Open Database Connectivity (ODBC), lorsque votre programme C++ gère une transaction distribuée. Le pilote ODBC Native Client dispose d’un gestionnaire de transactions qui est conforme à la norme XA de regroupements de traitement transactionnel distribué (PAO). Cette conformité est requise par MSDTC. En règle générale, toutes les commandes de gestion des transactions sont envoyées via ce pilote ODBC Native Client. La séquence est la suivante :

1. Votre application ODBC C++ native client démarre une transaction en appelant [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), en désactivant le mode de validation automatique.

2. L’application met à jour certaines données sur SQL Server X sur l’ordinateur A.

3. L’application met à jour certaines données sur SQL Server Y sur l’ordinateur B.
    - Si une mise à jour sur SQL Server Y échoue, toutes les mises à jour non validées sur les deux instances de SQL Server sont restaurées.

4. Enfin, l’application met fin à la transaction en appelant [SQLEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md), avec l’option SQL_COMMIT ou SQL_ROLLBACK.

_(1)_ MSDTC peut être appelé sans ODBC. Dans ce cas, MSDTC devient le gestionnaire de transactions et l’application n’utilise plus **SQLEndTran**.

### <a name="only-one-distributed-transaction"></a>Une seule transaction distribuée

Supposons que votre application ODBC C++ native client est inscrite dans une transaction distribuée. Ensuite, l’application est inscrite dans une deuxième transaction distribuée. Dans ce cas, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC native client conserve la transaction distribuée d’origine et s’inscrit dans la nouvelle transaction distribuée.

Pour plus d’informations, consultez le [Guide de référence du programmeur DTC](/previous-versions/windows/desktop/ms686108(v=vs.85)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>Alternative C# pour SQL Database dans le Cloud

MSDTC n’est pas pris en charge pour les Azure SQL Database ou Azure Synapse Analytics.

Toutefois, une transaction distribuée peut être créée pour SQL Database en faisant en sorte que votre programme C# utilise la classe .NET [System. transactions. TransactionScope](/dotnet/api/system.transactions.transactionscope).

### <a name="other-programming-languages"></a>Autres langages de programmation

Les autres langages de programmation suivants peuvent ne pas fournir de prise en charge des transactions distribuées avec le service SQL Database :

- C++ natif qui utilise des pilotes ODBC
- Serveur lié à l’aide de Transact-SQL
- Pilotes JDBC

## <a name="see-also"></a>Voir aussi

[Exécution de transactions (ODBC)](performing-transactions-in-odbc.md)