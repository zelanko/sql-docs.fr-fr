---
title: Méthode getTrustManagerClass (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getTrustManagerClass
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 567f5e7e3aca87b875e4f93c26d7caa5535a8c75
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978600"
---
# <a name="gettrustmanagerclass-method-sqlserverdatasource"></a>getTrustManagerClass, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de chaîne de la propriété de connexion TrustManagerClass.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getTrustManagerClass()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **chaîne** qui contient la valeur de la propriété de connexion TrustManagerClass, ou une valeur Null si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Si la propriété TrustManagerClass n’est pas définie, la méthode [getTrustManagerClass](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md) retourne la valeur Null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
