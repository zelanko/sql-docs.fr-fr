---
title: getConnection, méthode (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87d3dfc2183bdc00261417a024507b41ea5fde28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952743"
---
# <a name="getconnection-method-javalangstring-javalangstring"></a>Méthode getConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tente d’établir une connexion avec la source de données représentée par cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) à l’aide du nom d’utilisateur et du mot de passe donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *username*  
  
 **Chaîne** qui contient le nom de l’utilisateur.  
  
 *password*  
  
 **Chaîne** qui contient le mot de passe.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getConnection est spécifiée par la méthode getConnection dans l’interface javax. Sql. DataSource.  
  
 L’appel de la méthode getConnection avec un nom d’utilisateur ou un mot de passe non null remplace les propriétés de nom d’utilisateur et de mot de passe définies sur la classe SQLServerDataSource lors de l’initialisation de l’objet SQLServerConnection. Par exemple, si l’appelant a appelé [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) et [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) sur la source de données, puis appelle getConnection et fournit un nom d’utilisateur ou un mot de passe non Null, le nom d’utilisateur et le mot de passe définis par setUser et setPassword sont remplacés par ceux qui sont transmis à getConnection.  
  
> [!NOTE]  
>  Le nom d’utilisateur et le mot de passe définis au sein de l’URL par l’appel de la méthode [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md) ne sont pas modifiés dans ce cas.  
  
## <a name="see-also"></a>Voir aussi  
 [getConnection, méthode &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
