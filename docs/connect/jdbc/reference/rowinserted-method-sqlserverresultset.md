---
title: Méthode rowInserted (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b52007528ee5c3d3caaabc83b158e50156b664e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975697"
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si la ligne actuelle a eu une insertion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si une ligne a été insérée et que des insertions ont été détectées. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rowUpdated est spécifiée par la méthode rowUpdated dans l’interface java. Sql. ResultSet.  
  
 La valeur retournée dépend de la possibilité pour l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) de détecter des insertions visibles.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ne détecte pas les lignes insérées pour un type de curseur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
