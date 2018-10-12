---
title: Méthode Connect (SQLServerDriver) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: b4c1a7853925cfe6dbc97ab8f6c4c5b4f9147ac6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718337"
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
  
## <a name="return-value"></a>Valeur retournée  
 Objet Connection.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode de connexion est spécifiée par la méthode de connexion dans l’interface java.sql.Driver.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDriver, méthodes](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver, membres](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
