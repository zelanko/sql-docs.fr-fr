---
title: Méthode isAfterLast (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isAfterLast
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19f9d124-3184-4985-8b97-503a8ab8b4f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8542c6a2dc87e1f0d52049b27446acf2c1f909de
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80909855"
---
# <a name="isafterlast-method-sqlserverresultset"></a>isAfterLast, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère l’information indiquant si le curseur se trouve après la dernière ligne dans cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isAfterLast()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le curseur se trouve après la dernière ligne. **false** si le curseur se trouve à une autre position ou si le jeu de résultats ne contient aucune ligne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isAfterLast est spécifiée par la méthode isAfterLast de l’interface java.sql.ResultSet.  
  
 Si cette méthode est utilisée avec des curseurs dynamiques, dont les curseurs en lecture seule avant uniquement, et si la propriété de connexion selectMethod est définie sur « cursor », une exception se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
