---
title: Méthode getNClob (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: be01ce56-8f13-437b-8de6-246cda5f7830
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14f32e68272dfc6dd8f26c5020d1e18a5e4e5d8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47768847"
---
# <a name="getnclob-method-javalangstring"></a>Méthode getNClob (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur d’un paramètre **NCLOB** JDBC sous forme d’objet NClob dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.NClob getNClob(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 ANClobobject.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getNClob est spécifiée par la méthode getNClob de l’interface java.sql.CallableStatement.  
  
 Cette méthode prend uniquement en charge la récupération de **NCHAR**, **NVARCHAR**, **NTEXT**, et **XML** paramètres. L'appel de ces méthodes sur d'autres paramètres de type de données entraîne une exception.  
  
## <a name="see-also"></a> Voir aussi  
 [getNClob, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
