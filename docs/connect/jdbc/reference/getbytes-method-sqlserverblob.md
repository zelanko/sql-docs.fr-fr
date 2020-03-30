---
title: Méthode getBytes (SQLServerBlob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea1b810-b5c1-466d-bdc4-561468214632
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c4c7891c6d7454e0397406f9391fdfb60d0f0fc7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68213717"
---
# <a name="getbytes-method-sqlserverblob"></a>Méthode getBytes (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient les données de BLOB sous forme de tableau d'octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public byte[] getBytes(long pos,  
                       int length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pos*  
  
 Position de départ à 1 (et non 0).  
  
 *length*  
  
 Longueur des données à obtenir.  
  
## <a name="return-value"></a>Valeur de retour  
 Tableau **d’octets** contenant les données demandées.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBytes est spécifiée par la méthode getBytes de l’interface java.sql.Blob.  
  
 Si vous avez un BLOB de valeur Null ou de longueur zéro et que vous essayez d’obtenir exactement zéro octet à la position 1, un tableau **d’octets** vide (de longueur zéro) est retourné.  
  
 Si vous avez un BLOB de valeur Null ou de longueur zéro et que vous essayez d'obtenir une longueur d'octets quelconque à une position autre que la position 1, une exception de position est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerBlob, méthodes](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob, membres](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
