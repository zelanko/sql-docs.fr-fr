---
title: position, méthode (byte, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.position (byte[], long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e6056412f6ab2726112d5286f2f52c83ff6691cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66802464"
---
# <a name="position-method-byte-long"></a>position, méthode (byte, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la position d’un modèle spécifié dans le BLOB, en fonction du modèle de tableau **d’octets** donné et de l’index de départ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bPattern*  
  
 Le modèle à rechercher.  
  
 *start*  
  
 Index de départ pour la recherche.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur **long** de la position à laquelle le modèle a été trouvé, ou -1 s’il n’a pas été trouvé.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode de position est spécifiée par la méthode de position dans l’interface java.sql.Blob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode position &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [SQLServerBlob, méthodes](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob, membres](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
