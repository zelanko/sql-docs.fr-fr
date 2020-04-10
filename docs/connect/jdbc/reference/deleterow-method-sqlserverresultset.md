---
title: Méthode deleteRow (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c6f5cc2d3b58f553f74288c2c86e7b6d9d32d72
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922165"
---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow, méthode (SQLServerResultSet)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Supprime la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) et de la base de données sous-jacente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
public void deleteRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode deleteRow est spécifiée par la méthode deleteRow de l’interface java.sql.ResultSet.  
  
 Cette méthode ne peut pas être appelée lorsque le curseur se trouve sur la ligne d'insertion.  
  
 Si vous utilisez des curseurs de jeu de clés, cette méthode fait apparaître un vide dans le jeu de résultats. Vous pouvez tester la présence de ce vide à l’aide de la méthode [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md). Les numéros des lignes dans le jeu de résultats ne changent pas.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
