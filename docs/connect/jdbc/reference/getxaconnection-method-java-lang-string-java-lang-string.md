---
title: getXAConnection, méthode (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXADataSource.getXAConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276e0093-3d42-4f73-acc4-2b5b98245b40
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: db13bdb3a1039abf1b07616d4cd94001833e3600
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801710"
---
# <a name="getxaconnection-method-javalangstring-javalangstring"></a>Méthode getXAConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Essaie d'établir une connexion de base de données physique à l'aide du nom d'utilisateur et du mot de passe donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public javax.sql.XAConnection getXAConnection(java.lang.String user,  
                                              java.lang.String password)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *user*  
  
 **Chaîne** qui contient le nom de l’utilisateur.  
  
 *password*  
  
 **Chaîne** qui contient le mot de passe.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet XAConnection.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getXAConnection est spécifiée par la méthode getXAConnection dans l’interface javax.sql.XADataSource.  
  
> [!NOTE]  
>  Cette méthode est généralement appelée par les implémentations de regroupement de connexions XA et non par le code d'application JDBC normal.  
  
## <a name="see-also"></a>Voir aussi  
 [getXAConnection, méthode &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [SQLServerXADataSource, méthodes](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [SQLServerXADataSource, membres](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [SQLServerXADataSource, classe](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
