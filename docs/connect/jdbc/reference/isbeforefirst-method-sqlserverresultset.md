---
description: isBeforeFirst, méthode (SQLServerResultSet)
title: Méthode isBeforeFirst (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isBeforeFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e0e2bd28-6949-47dc-b9dd-145ffb337069
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7519aec8d29a72ed45a0f56eadfcbfdf85c9c780
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433641"
---
# <a name="isbeforefirst-method-sqlserverresultset"></a>isBeforeFirst, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère l’information indiquant si le curseur se trouve avant la première ligne dans cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isBeforeFirst()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le curseur se trouve avant la première ligne. **false** si le curseur se trouve à une autre position ou si le jeu de résultats ne contient aucune ligne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isBeforeFirst est spécifiée par la méthode isBeforeFirst de l’interface java.sql.ResultSet.  
  
 Si cette méthode est utilisée avec des curseurs dynamiques, dont les curseurs en lecture seule avant uniquement, et si la propriété de connexion selectMethod est définie sur « cursor », une exception se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
