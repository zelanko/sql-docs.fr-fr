---
title: Méthode position (java.sql.NClob, long) | Documents Microsoft
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
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bcac66bf3ca49b7837d3b552d708cea16422de1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="position-method-javasqlnclob-long"></a>Méthode position (java.sql.NClob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la position de caractère à laquelle le texte spécifié **NClob** objet *searchstr* s’affiche dans cette **NClob** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
long position(java.sql.NClob searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *searchstr*  
  
 Un objet NClob à rechercher.  
  
 *start*  
  
 Position à laquelle démarrer la recherche ; la première position est 1.  
  
## <a name="return-value"></a>Valeur retournée  
 Position à laquelle la sous-chaîne doit s'afficher, ou -1 si elle est absente. La première position est 1.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Position de cette méthode est spécifiée par la méthode de position dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode position &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [Méthodes SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membres de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
