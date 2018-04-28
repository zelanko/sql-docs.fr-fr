---
title: getBinaryStream (méthode) (long, long) | Documents Microsoft
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
ms.assetid: 30bc8882-04b4-4efd-95e4-7d3a2a8c1d47
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8d514ab1f095cf51a52993571f801ae81101fa14
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getbinarystream-method-long-long"></a>Méthode getBinaryStream (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un objet de flux d'entrée qui contient une valeur BLOB partielle à l'aide de la position de début spécifiée et de la longueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.InputStream getBinaryStream(long pos, long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 Décalage du premier octet de la valeur partielle à récupérer.  
  
 *length*  
  
 Longueur en octets de la valeur partielle à récupérer.  
  
## <a name="return-value"></a>Valeur retournée  
 Flux d'entrée contenant les données du BLOB.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBinaryStream est spécifiée par la méthode getBinaryStream dans l’interface java.sql.Blob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Membres de SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
