---
title: Méthode getNClob (java.lang.String) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: be01ce56-8f13-437b-8de6-246cda5f7830
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aadea5e4a373935f0b00dd3604885589afb9bd11
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getnclob-method-javalangstring"></a>Méthode getNClob (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur d’un JDBC **NCLOB** paramètre en tant qu’objet NClob dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.NClob getNClob(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 ANClobobject.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNClob est spécifiée par la méthode getNClob dans l’interface java.sql.CallableStatement.  
  
 Cette méthode prend uniquement en charge la récupération de **NCHAR**, **NVARCHAR**, **NTEXT**, et **XML** paramètres. L'appel de ces méthodes sur d'autres paramètres de type de données entraîne une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getNClob &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
