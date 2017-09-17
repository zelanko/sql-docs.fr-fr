---
title: "Méthode setString (long, java.lang.String) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerClob.setString (long, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1b2190e9-5ace-497a-8554-0e913ea9b0cb
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0b1bcd2dc8f6e6509099eb4529e57335942c9d6d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring"></a>Méthode setString (long, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Écrit la donnée **chaîne** dans le CLOB, en commençant à la position donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int setString(long pos,  
                     java.lang.String s)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 Position à laquelle démarrer l'écriture dans l'objet CLOB.  
  
 *s*  
  
 Le **chaîne** à écrire dans le CLOB.  
  
## <a name="return-value"></a>Valeur retournée  
 Nombre de caractères écrits.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString dans l’interface java.sql.Clob.  
  
 Les données de caractères sont remplacées en démarrant à la position spécifiée et peuvent dépasser la longueur initiale de l'objet CLOB. La spécification d'une valeur position+1 permet d'ajouter la chaîne. La spécification d'une valeur position+2 ou supérieure (ou de zéro ou d'une valeur inférieure) entraîne la levée d'une erreur de position.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setString &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [Méthodes SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membres de SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
