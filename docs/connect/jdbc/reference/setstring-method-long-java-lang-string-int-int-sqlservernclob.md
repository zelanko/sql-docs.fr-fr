---
title: Méthode setString (long, java.lang.String, int, int) - NClob | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 074983f08e837f3a895ddc8884e5ac140033c51e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972743"
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>Méthode setString (long, java.lang.String, int, int) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Écrit la chaîne spécifiée dans le NCLOB, en commençant à la position spécifiée, en fonction du décalage et de la longueur spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pos*  
  
 Position à laquelle commencera l’écriture dans le **NCLOB** ; la première position est 1.  
  
 *str*  
  
 String à écrire sur le **NCLOB**.  
  
 *offset*  
  
 Décalage dans *str* à respecter pour démarrer la lecture des caractères à écrire.  
  
 *len*  
  
 Nombre de caractères à écrire.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setString est spécifiée par la méthode setString de l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
