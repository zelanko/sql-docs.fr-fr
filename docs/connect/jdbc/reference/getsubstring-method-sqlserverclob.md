---
title: Méthode getSubString (SQLServerClob) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerClob.getSubString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf915590-a883-4403-befa-5b5bb42f34d8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57bfbc4553d33005a81ee71864551c1b91b481f6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getsubstring-method-sqlserverclob"></a>Méthode getSubString (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une copie de la sous-chaîne spécifiée dans le CLOB, en fonction de la position de départ donnée et du nombre de caractères à copier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getSubString(long pos,  
                                     int length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 Premier caractère de la sous-chaîne à extraire. Le premier caractère est à la position 1.  
  
 *length*  
  
 Nombre des caractères consécutifs à copier.  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui est la sous-chaîne spécifiée dans l’objet CLOB.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSubString est spécifiée par la méthode getSubString dans l’interface java.sql.Clob.  
  
 La tentative d'obtention de zéro caractère depuis un CLOB avec une valeur Null ou de longueur zéro retourne une chaîne vide. La tentative d'obtention d'une longueur de caractères quelconque à n'importe quelle position autre que la position 1 dans un CLOB de longueur zéro entraîne la levée d'une exception de position.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membres de SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
