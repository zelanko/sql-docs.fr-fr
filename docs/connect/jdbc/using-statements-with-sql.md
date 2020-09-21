---
title: Utilisation d'instructions avec SQL
description: Découvrez une vue d’ensemble de l’utilisation de différents types d’instructions SQL avec le Pilote Microsoft JDBC pour SQL Server.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49ab0f6367353847bdf3a9e0a7aff13975b4d711
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435285"
---
# <a name="using-statements-with-sql"></a>Utilisation d'instructions avec SQL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Quand vous utilisez les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] et les instructions SQL incluses, vous pouvez utiliser différentes classes. La classe que vous utilisez dépend du type d'instruction SQL que vous souhaitez exécuter.  
  
Si votre instruction SQL ne contient pas de paramètres IN, utilisez la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Dans le cas contraire, utilisez la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
> [!NOTE]  
> Si vous devez utiliser des instructions SQL contenant à la fois des paramètres IN et OUT, vous devez les implémenter en tant que procédures stockées et les appeler à l’aide de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Pour plus d’informations sur les procédures stockées , consultez [Utiliser des instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
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
