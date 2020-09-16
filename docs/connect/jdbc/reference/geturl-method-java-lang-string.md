---
description: Méthode getURL (java.lang.String)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 18bf85b53eb15831327970cfa1c1ab90590df157
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433841"
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
  
## <a name="return-value"></a>Valeur de retour  
 Objet URL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getURL est spécifiée par la méthode getURL de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [getURL, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
