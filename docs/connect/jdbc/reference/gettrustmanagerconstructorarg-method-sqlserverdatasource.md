---
title: gettrustmanagerconstructorarg, méthode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getTrustManagerConstructorArg
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 24efba087c6e2f988e25517ceffb61463b0ec935
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786203"
---
# <a name="gettrustmanagerconstructorarg-method-sqlserverdatasource"></a>getTrustManagerConstructorArg, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de chaîne de la propriété de connexion TrustManagerConstructorArg.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getTrustManagerConstructorArg()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **chaîne** qui contient la valeur de la propriété de connexion TrustManagerConstructorArg, ou null si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Si la propriété TrustManagerClass n’est pas définie, le [getTrustManagerConstructorArg](../../../connect/jdbc/reference/gettrustmanagerconstructorarg-method-sqlserverdatasource.md) méthode retourne la valeur null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
