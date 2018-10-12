---
title: getbinarystream, méthode (long, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 30bc8882-04b4-4efd-95e4-7d3a2a8c1d47
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd171495bb8dde28a30299b0107d91cce9dd472e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757167"
---
# <a name="getbinarystream-method-long-long"></a>Méthode getBinaryStream (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un objet de flux d'entrée qui contient une valeur BLOB partielle à l'aide de la position de début spécifiée et de la longueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.InputStream getBinaryStream(long pos, long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Points de vente*  
  
 Décalage du premier octet de la valeur partielle à récupérer.  
  
 *length*  
  
 Longueur en octets de la valeur partielle à récupérer.  
  
## <a name="return-value"></a>Valeur retournée  
 Flux d'entrée contenant les données du BLOB.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getBinaryStream est spécifiée par la méthode getBinaryStream dans l’interface java.sql.Blob.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerBlob, méthodes](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob, membres](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
