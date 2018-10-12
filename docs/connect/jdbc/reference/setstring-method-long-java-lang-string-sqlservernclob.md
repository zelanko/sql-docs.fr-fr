---
title: Méthode setString (long, java.lang.String) - NClob | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 698073b2-3f0c-449c-ad68-48144698fe8f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 151ff8f36ad3397321dc168b46a949de38e10bd6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689897"
---
# <a name="setstring-method-long-javalangstring-sqlservernclob"></a>Méthode setString (long, java.lang.String) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Écrit le texte spécifié **chaîne** à la **NCLOB** en commençant à la position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int setString(long pos,  
              java.lang.String str)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Points de vente*  
  
 Position à laquelle commencera l’écriture dans le **NCLOB** ; la première position est 1.  
  
 *str*  
  
 String à écrire sur le **NCLOB**.  
  
## <a name="return-value"></a>Valeur retournée  
 Nombre de caractères écrits.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setString est spécifiée par la méthode setString dans l’interface java.sql.NClob.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
