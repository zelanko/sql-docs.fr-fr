---
title: Méthode getUser (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getUser
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5562f9b19b59096784ad3dd2a09e9135a7e07cf2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978185"
---
# <a name="getuser-method-sqlserverdatasource"></a>Méthode getUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom d'utilisateur qui est utilisé pour la connexion à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getUser()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **Chaîne** qui contient le nom de l’utilisateur.  
  
## <a name="remarks"></a>Notes  
 La méthode [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) définit le nom d’utilisateur à utiliser lors de la connexion à l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la valeur de nom d'utilisateur n'est pas définie, la méthode getUser retourne la valeur par défaut Null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
