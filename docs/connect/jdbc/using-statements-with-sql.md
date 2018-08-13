---
title: Utilisation d’instructions avec SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d044c1747b13f94c6f7feb902144d51b50af870
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662221"
---
# <a name="using-statements-with-sql"></a>Utilisation des instructions avec SQL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Quand vous utilisez les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en utilisant le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] et les instructions SQL incluses, vous pouvez utiliser différentes classes. La classe que vous utilisez dépend du type d'instruction SQL que vous souhaitez exécuter.  
  
Si votre instruction SQL ne contient pas de paramètres IN, utilisez la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Dans le cas contraire, utilisez la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
> [!NOTE]  
> Si vous devez utiliser des instructions SQL contenant à la fois des paramètres IN et OUT, vous devez les implémenter en tant que procédures stockées et les appeler à l’aide de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Pour plus d’informations sur l’utilisation de procédures stockées, consultez [à l’aide d’instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
Les sections suivantes décrivent les différents scénarios relatifs à l’utilisation des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] à l’aide d’instructions SQL.  

## <a name="in-this-section"></a>Dans cette section  

| Rubrique                                                                                                                        | Description                                                       |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Utilisation d’une instruction SQL sans paramètres](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)                 | Décrit la méthode d'utilisation des instructions SQL ne contenant pas de paramètres.   |
| [Utilisation d’une instruction SQL avec des paramètres](../../connect/jdbc/using-an-sql-statement-with-parameters.md)                       | Décrit la méthode d'utilisation des instructions SQL contenant des paramètres.      |
| [Utilisation d’une instruction SQL pour modifier des objets de base de données](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md) | Décrit la méthode d'utilisation des instructions SQL pour modifier les objets de base de données.   |
| [Utilisation d’une instruction SQL pour modifier des données](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)                         | Décrit la méthode d'utilisation des instructions SQL pour modifier des données dans une base de données. |
  
## <a name="see-also"></a> Voir aussi

[Utilisation d’instructions avec le pilote JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
