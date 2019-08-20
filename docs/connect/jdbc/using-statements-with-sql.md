---
title: Utilisation d’instructions avec SQL | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 553c0e742b34406b23a68f1403c372dcc7080088
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69025830"
---
# <a name="using-statements-with-sql"></a>Utilisation d'instructions avec SQL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Quand vous utilisez les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] et les instructions SQL incluses, vous pouvez utiliser différentes classes. La classe que vous utilisez dépend du type d'instruction SQL que vous souhaitez exécuter.  
  
Si votre instruction SQL ne contient pas de paramètres IN, utilisez la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Dans le cas contraire, utilisez la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
> [!NOTE]  
> Si vous devez utiliser des instructions SQL contenant à la fois des paramètres IN et OUT, vous devez les implémenter en tant que procédures stockées et les appeler à l’aide de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Pour plus d’informations sur l’utilisation des procédures stockées, consultez [utilisation d’instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
Les sections suivantes décrivent les différents scénarios relatifs à l’utilisation des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’instructions SQL.  

## <a name="in-this-section"></a>Dans cette section  

| Rubrique                                                                                                                        | Description                                                       |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Utilisation d'une instruction SQL sans paramètres](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)                 | Décrit la méthode d'utilisation des instructions SQL ne contenant pas de paramètres.   |
| [Utilisation d'une instruction SQL avec paramètres](../../connect/jdbc/using-an-sql-statement-with-parameters.md)                       | Décrit la méthode d'utilisation des instructions SQL contenant des paramètres.      |
| [Utilisation d'une instruction SQL pour modifier les objets de base de données](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md) | Décrit la méthode d'utilisation des instructions SQL pour modifier les objets de base de données.   |
| [Utilisation d'une instruction SQL pour modifier des données](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)                         | Décrit la méthode d'utilisation des instructions SQL pour modifier des données dans une base de données. |
  
## <a name="see-also"></a>Voir aussi

[Utilisation d'instructions avec le pilote JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
