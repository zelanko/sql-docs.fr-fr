---
title: SQLServerResultSet, classe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eaffcff1-286c-459f-83da-3150778480c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e0a2185037f54aa7ed975667c0bdd5fb921c845
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970614"
---
# <a name="sqlserverresultset-class"></a>Classe SQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente un jeu de résultats JDBC.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Implémente :** [ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final class SQLServerResultSet  
```  
  
## <a name="remarks"></a>Notes  
 Il existe deux types de jeux de résultats : côté client et côté serveur.  
  
 Les jeux de résultats côté client sont utilisés lorsque la mémoire du processus client dispose d'assez de place pour contenir les résultats. Ces résultats offrent de meilleures performances en termes de rapidité et sont lus dans leur intégralité par [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] dans la base de données. Ces jeux de résultats n'imposent aucune charge supplémentaire pour la base de données puisqu'aucun curseur n'est créé côté serveur. Cependant, ces types de jeux de résultats ne peuvent pas être mis à jour.  
  
 Les jeux de résultats côté serveur peuvent être utilisés lorsque les résultats sont trop importants pour être inclus dans la mémoire du processus client ou lorsque le jeu de résultats doit pouvoir être mis à jour. Avec ce type de jeu de résultats, le pilote JDBC crée un curseur côté serveur et extrait les lignes du jeu de résultats de façon transparente au fur et à mesure que l'utilisateur fait défiler les résultats.  
  
 La classe SQLServerResultSet fournit de nombreuses méthodes permettant de mettre à jour le jeu de résultats avec n’importe quel type de données Java natif et la plupart des types d’objets Java.  
  
 Cette classe prend en charge le désencapsulage dans l’interface SQLServerResultSet Class, ISQLServerResultSet et Java. Sql. ResultSet. Pour plus d’informations, consultez [wrappers et interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
