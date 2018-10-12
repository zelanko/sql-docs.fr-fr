---
title: Méthode getNString (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b351e999-85bf-498b-915a-f91d89134bce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8416de108cd4456599375f54c7afc0b4a5fefa8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730497"
---
# <a name="getnstring-method-javalangstring"></a>Méthode getNString (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de l’élément désigné **NCHAR**, **NVARCHAR**, ou **LONGNVARCHAR** paramètre sous forme de chaîne dans le Java en langage de programmation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.lang.String getNString(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 AStringobject.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getNString est spécifiée par la méthode getNString de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a> Voir aussi  
 [getNString, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, méthodes](../../../connect/jdbc/reference/sqlservercallablestatement-methods.md)  
  
  
