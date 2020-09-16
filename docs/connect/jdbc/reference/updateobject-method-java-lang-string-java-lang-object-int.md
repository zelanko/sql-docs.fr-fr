---
description: Méthode updateObject (java.lang.String, java.lang.Object, int)
title: updateObject, méthode (java.lang.String, java.lang.Object, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateObject (java.lang.String, java.lang.Object, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 27283ce1-637e-4e2c-91ee-8ad379114ac5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbc070f71830113875add1d4711671832ae4de12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478294"
---
# <a name="updateobject-method-javalangstring-javalangobject-int"></a>Méthode updateObject (java.lang.String, java.lang.Object, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur **Object** en fonction du nom de colonne et de l’échelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateObject(java.lang.String columnName,  
                         java.lang.Object x,  
                         int scale)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 Valeur **String** qui contient le nom de la colonne.  
  
 *obj*  
  
 Valeur **Object**.  
  
 *scale*  
  
 Pour les types java.sql.Types.DECIMAL ou java.sql.Types.NUMERIC, il s'agit du nombre de chiffres après la virgule décimale. Pour tous les autres types, cette valeur est ignorée.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateObject est spécifiée par la méthode updateObject de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateObject, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
