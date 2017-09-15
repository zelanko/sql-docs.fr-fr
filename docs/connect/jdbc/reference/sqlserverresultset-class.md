---
title: Classe SQLServerResultSet | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaffcff1-286c-459f-83da-3150778480c9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac9db37012a51c8ba365b22dd7e56b30ae5b5b6d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverresultset-class"></a>Classe SQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente un jeu de résultats JDBC.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Implémente :** [ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final class SQLServerResultSet  
```  
  
## <a name="remarks"></a>Notes  
 Il existe deux types de jeux de résultats : côté client et côté serveur.  
  
 Les jeux de résultats côté client sont utilisés lorsque la mémoire du processus client dispose d'assez de place pour contenir les résultats. Ces résultats fournissent de meilleures performances et sont lus par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] dans leur intégralité à partir de la base de données. Ces jeux de résultats n'imposent aucune charge supplémentaire pour la base de données puisqu'aucun curseur n'est créé côté serveur. Cependant, ces types de jeux de résultats ne peuvent pas être mis à jour.  
  
 Les jeux de résultats côté serveur peuvent être utilisés lorsque les résultats sont trop importants pour être inclus dans la mémoire du processus client ou lorsque le jeu de résultats doit pouvoir être mis à jour. Avec ce type de jeu de résultats, le pilote JDBC crée un curseur côté serveur et extrait les lignes du jeu de résultats de façon transparente au fur et à mesure que l'utilisateur fait défiler les résultats.  
  
 La classe SQLServerResultSet fournit de nombreuses méthodes permettant de mettre à jour le jeu de résultats avec tout type de données Java natif et de nombreux types d’objets Java.  
  
 Cette classe prend en charge la Désencapsulation dans la classe SQLServerResultSet, interface ISQLServerResultSet et interface java.sql.ResultSet. Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
