---
title: "Méthode setString (long, java.lang.String) - NClob | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 698073b2-3f0c-449c-ad68-48144698fe8f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 383bd895015a5b66347bfb310791b8145de32247
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring-sqlservernclob"></a>Méthode setString (long, java.lang.String) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Écrit le **chaîne** à la **NCLOB** en commençant à la position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int setString(long pos,  
              java.lang.String str)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 Position à laquelle démarrer l’écriture dans le **NCLOB**; la première position est 1.  
  
 *Str*  
  
 La chaîne à écrire dans le **NCLOB**.  
  
## <a name="return-value"></a>Valeur retournée  
 Nombre de caractères écrits.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membres de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
