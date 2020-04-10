---
title: Méthode updateFloat (int, float) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateFloat (int, float)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c9ddcd7d-1dd4-491a-99ff-6cce7f67a73b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b8cb92a23a9d3c3c9725dc555ff66c967ed4ecd
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927869"
---
# <a name="updatefloat-method-int-float"></a>Méthode updateFloat (int, float)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur **float** en fonction de l’index de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateFloat(int index,  
                        float x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 **int** indiquant l’index de la colonne.  
  
 *x*  
  
 Valeur **flottante**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateFloat est spécifiée par la méthode updateFloat de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateFloat, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
