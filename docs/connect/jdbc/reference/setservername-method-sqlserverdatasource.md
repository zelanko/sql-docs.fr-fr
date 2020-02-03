---
title: Méthode setServerName (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 344ae0104f527739bf3a954ed9138252d7efb58e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972931"
---
# <a name="setservername-method-sqlserverdatasource"></a>Méthode setServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom de l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *serverName*  
  
 **Chaîne** qui contient le nom du serveur.  
  
## <a name="remarks"></a>Notes  
 Le nom du serveur correspond au nom d’hôte de l’ordinateur cible qui exécute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si la propriété serverName n’est pas définie, [getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md) retourne la valeur par défaut, null.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
