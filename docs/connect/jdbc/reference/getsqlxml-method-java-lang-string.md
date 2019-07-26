---
title: Méthode getSQLXML (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f56b192a-3255-4215-b552-8e494fbca083
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 125584fd3ad858a4242f6d85e755b3ec04e50ab1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979645"
---
# <a name="getsqlxml-method-javalangstring"></a>Méthode getSQLXML (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné sous forme d’objet SQLXML en fonction du nom de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 **Chaîne** qui indique le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 ASQLXMLobject.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSQLXML est spécifiée par la méthode getSQLXML de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [getSQLXML, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
