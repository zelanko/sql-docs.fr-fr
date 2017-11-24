---
title: "Méthode setString (long, java.lang.String, int, int) - NClob | Documents Microsoft"
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
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a5945b09f75fefde2b87387d02ca45ad58b0cc0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>Méthode setString (long, java.lang.String, int, int) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Écrit la chaîne spécifiée dans le NCLOB en commençant à la position spécifiée, en fonction de l’offset spécifié et la longueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 Position à laquelle démarrer l’écriture dans le **NCLOB**; la première position est 1.  
  
 *Str*  
  
 La chaîne à écrire dans le **NCLOB**.  
  
 *décalage*  
  
 Offset dans *str* pour démarrer la lecture des caractères à écrire.  
  
 *Len*  
  
 Nombre de caractères à écrire.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membres de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
