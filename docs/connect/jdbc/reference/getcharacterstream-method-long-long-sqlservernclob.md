---
title: getCharacterStream, méthode (long, long) (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5071cf1e570418723ced2602f6b88a5a2227069c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633617"
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>Méthode getCharacterStream (long, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne les données **NCLOB** sous forme d’objet **Reader** ou de flux de caractères avec une position et une longueur spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Points de vente*  
  
 Un **long** qui indique le décalage vers le premier caractère de la valeur partielle à récupérer.  
  
 *length*  
  
 Un **long** qui indique la longueur en caractères de la valeur partielle à récupérer.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet Reader contenant les données **NCLOB**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getCharacterStream est spécifiée par la méthode getCharacterStream dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a> Voir aussi  
 [getCharacterStream, méthode &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
