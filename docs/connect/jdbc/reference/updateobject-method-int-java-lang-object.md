---
title: "Méthode updateObject (int, java.lang.Object) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.updateObject (int, java.lang.Object)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 4993dfe1-2232-4b3c-b931-dfdb35dd225a
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c59092816c8b01740b9b5375b430fb46c82b704c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="updateobject-method-int-javalangobject"></a>Méthode updateObject (int, java.lang.Object)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une **objet** valeur en fonction de l’index de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateObject(int index,  
                         java.lang.Object obj)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de colonne.  
  
 *obj*  
  
 Un **objet** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateObject est spécifiée par la méthode updateObject dans l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode updateObject &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
