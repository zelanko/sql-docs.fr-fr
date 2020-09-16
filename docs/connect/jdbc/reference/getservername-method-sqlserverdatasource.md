---
description: Méthode getServerName (SQLServerDataSource)
title: Méthode getServerName (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f8e2045d2c296386f13907ce3b95923a5b58826e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434601"
---
# <a name="getservername-method-sqlserverdatasource"></a>Méthode getServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom de l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** qui contient le nom du serveur ou Null si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Le nom du serveur correspond au nom d’hôte de l’ordinateur cible qui exécute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la propriété getServerName n’est pas définie, getServerName retourne la valeur par défaut, qui est Null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
