---
title: Méthode getURL (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getURL (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb709f6b-64e1-4d0c-a704-290891627dd7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ec61791897011781cbe93776bb58bfdd144bd6e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978288"
---
# <a name="geturl-method-javalangstring"></a>Méthode getURL (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné sous forme d’objet URL dans le langage de programmation Java en fonction du nom de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.net.URL getURL(java.lang.String s)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *s*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet URL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getURL est spécifiée par la méthode getURL de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [getURL, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
