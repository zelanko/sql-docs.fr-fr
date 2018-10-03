---
title: Méthode setUser (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f3953763dc1b8a0d24e4c335b5b465c49707174
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784157"
---
# <a name="setuser-method-sqlserverdatasource"></a>Méthode setUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom d'utilisateur utilisé pour la connexion à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *user*  
  
 **Chaîne** qui contient le nom de l’utilisateur.  
  
## <a name="remarks"></a>Notes   
 La méthode setUser définit le nom d’utilisateur qui sera utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la valeur du nom d’utilisateur n’est pas définie, la méthode [getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md) retourne la valeur par défaut Null.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
