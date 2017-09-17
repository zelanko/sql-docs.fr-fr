---
title: "Méthode setCharacterStream (SQLServerNClob) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54ea45119a144852daff92dac5037b6f7407d259
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setcharacterstream-method-sqlservernclob"></a>Méthode setCharacterStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un flux de données à utiliser pour écrire un flux de caractères Unicode à la **NCLOB** que cette valeur **java.sql.NClob** objet représente, en commençant à la position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bons de commande*  
  
 Position à laquelle démarrer l’écriture dans le **NCLOB** valeur ; la première position est 1.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet Writer qui représente le flux dans lequel les caractères chiffrés Unicode peut être écrites.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCharacterStream est spécifiée par la méthode setCharacterStream dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membres de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
