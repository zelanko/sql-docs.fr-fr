---
title: connect, méthode (SQLServerDriver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.connect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43813a4c-1cc7-4659-ba27-f1786f1371eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 518be09d4a4929a06866eec253a49a39d7865263
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955419"
---
# <a name="connect-method-sqlserverdriver"></a>Méthode connect (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Établit une connexion à la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Connection connect(java.lang.String Url,  
                                   java.util.Properties suppliedProperties)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Url*  
  
 Valeur **String** contenant l’URL utilisée pour la connexion à la base de données.  
  
 *suppliedProperties*  
  
 Ensemble de paires de valeurs de chaîne utilisé comme arguments de connexion.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet Connection.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode connect est spécifiée par la méthode connect dans l’interface java.sql.Driver.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDriver, méthodes](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver, membres](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
