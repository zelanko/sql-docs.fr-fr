---
title: Méthode moveToInsertRow (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bc8420b9f79ce61874dbb03e73924e7be6eca96
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976783"
---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>moveToInsertRow, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Déplace le curseur vers la ligne d'insertion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode moveToInsertRow est spécifiée par la méthode moveToInsertRow de l’interface java.sql.ResultSet.  
  
 La position actuelle du curseur est mémorisée lorsque le curseur est placé sur la ligne d'insertion. La ligne d'insertion est une ligne spéciale associée à un jeu de résultats pouvant être mis à jour. Elle constitue essentiellement un tampon dans lequel une nouvelle ligne peut être construite en appelant les méthodes updater avant d'ajouter la ligne au jeu de résultats.  
  
 Seules les méthodes updater, getter et [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) peuvent être appelées lorsque le curseur se trouve sur la ligne d’insertion. Toutes les colonnes d’un jeu de résultats doivent recevoir une valeur chaque fois que cette méthode est appelée et avant d’appeler insertRow. Une méthode updater doit être appelée pour qu'une méthode getter puisse être elle-même appelée sur une valeur de colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
