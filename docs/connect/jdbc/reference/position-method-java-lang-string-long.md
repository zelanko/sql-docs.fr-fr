---
title: "Méthode position (java.lang.String, long) | Documents Microsoft"
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
apiname: SQLServerClob.position (java.lang.String, long)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 86fad8ed-375a-42e1-b40e-1fa085957a2c
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b9769bdc5bde6059b08198139d91975028d6b211
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="position-method-javalangstring-long"></a>Méthode position (java.lang.String, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la position de caractère de la sous-chaîne spécifiée dans l'objet CLOB, en fonction de la position de départ donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public long position(java.lang.String searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *searchstr*  
  
 La sous-chaîne à rechercher.  
  
 *Démarrer*  
  
 Position à laquelle démarrer la recherche ; la première position est 1.  
  
## <a name="return-value"></a>Valeur retournée  
 Position à laquelle la sous-chaîne doit s'afficher, ou -1 si elle est absente. La première position est 1.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Position de cette méthode est spécifiée par la méthode de position dans l’interface java.sql.Clob.  
  
## <a name="see-also"></a>Voir aussi  
 [Placez la méthode &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [Méthodes SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membres de SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
