---
title: setcharacterstream, méthode (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 081da23826951c5c8c4d4872de1c28a771a2958b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720917"
---
# <a name="setcharacterstream-method-sqlservernclob"></a>Méthode setCharacterStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un flux servant à écrire un flux de caractères Unicode dans la valeur **NCLOB** représentée par cet objet **java.sql.NClob**, en commençant à la position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Points de vente*  
  
 Position à laquelle commencera l’écriture dans la valeur **NCLOB** ; la première position est 1.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet Writer représentant le flux sur lequel peuvent être écrits les caractères encodés Unicode.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setCharacterStream est spécifiée par la méthode setCharacterStream dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
