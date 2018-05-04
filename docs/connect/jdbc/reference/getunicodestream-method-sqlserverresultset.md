---
title: getUnicodeStream (méthode) (SQLServerResultSet) | Documents Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerResultSet.getUnicodeStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0dd61865-663b-47e2-b417-e9df418894cc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 52900f4e9ca91e4dc91ca939f0609ed42bdb1084
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getunicodestream-method-sqlserverresultset"></a>getUnicodeStream (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de la colonne désignée dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet en tant que flux de caractères Unicode.  
  
> [!NOTE]  
>  Cette méthode a été déconseillée dans la spécification JDBC et son appel entraîne la levée d'une exception « Non implémenté ». Au lieu de cela, vous devez utiliser le [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) (méthode).  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Nom| Description|  
|----------|-----------------|  
|[Méthode getUnicodeStream &#40;int&#41;](../../../connect/jdbc/reference/getunicodestream-method-int.md)|Récupère la valeur de l’index de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet en tant que flux de caractères Unicode.|  
|[Méthode getUnicodeStream &#40;java.lang.String&#41;](../../../connect/jdbc/reference/getunicodestream-method-java-lang-string.md)|Récupère la valeur du nom de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet en tant que flux de caractères Unicode.|  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
