---
title: "Utilisation d’instructions avec SQL | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5cba782d32a60b2bbdcf61276db6a1989f82c50b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-statements-with-sql"></a>Utilisation des instructions avec SQL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lorsque vous travaillez avec des données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données à l’aide de la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] et les instructions SQL incluses, il existe différentes classes que vous pouvez utiliser. La classe que vous utilisez dépend du type d'instruction SQL que vous souhaitez exécuter.  
  
 Si votre instruction SQL ne contient aucun paramètre IN, utilisez la [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) de classe, mais s’il ne contient pas de paramètres, utilisez le [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe.  
  
> [!NOTE]  
>  Si vous devez utiliser des instructions SQL contenant à la fois dans et les paramètres OUT, vous devez les implémenter tant que procédures stockées et les appeler à l’aide de la [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe. Pour plus d’informations sur l’utilisation des procédures stockées, consultez [à l’aide d’instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
 Les sections suivantes décrivent les différents scénarios d’utilisation des données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données à l’aide d’instructions SQL.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[À l’aide d’une instruction SQL sans paramètres](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)|Décrit la méthode d'utilisation des instructions SQL ne contenant pas de paramètres.|  
|[À l’aide d’une instruction SQL avec des paramètres](../../connect/jdbc/using-an-sql-statement-with-parameters.md)|Décrit la méthode d'utilisation des instructions SQL contenant des paramètres.|  
|[À l’aide d’une instruction SQL pour modifier des objets de base de données](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md)|Décrit la méthode d'utilisation des instructions SQL pour modifier les objets de base de données.|  
|[À l’aide d’une instruction SQL pour modifier des données](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)|Décrit la méthode d'utilisation des instructions SQL pour modifier des données dans une base de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’instructions avec le pilote JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

