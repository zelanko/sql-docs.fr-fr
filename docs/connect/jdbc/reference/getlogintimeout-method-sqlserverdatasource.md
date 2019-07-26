---
title: Méthode getLoginTimeout (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5fe82d2709aa8efa32408a9d9d86f0f660bed823
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982556"
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>Méthode getLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nombre de secondes pendant lesquelles cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) patiente lors de la tentative de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur **int** représentant le nombre de secondes à attendre.  
  
## <a name="remarks"></a>Notes  
 Si l'application ne spécifie pas explicitement une valeur de délai d'attente, cette méthode retourne une valeur par défaut de 15 secondes.  
  
 Cette méthode getLoginTimeout est spécifiée par la méthode getLoginTimeout dans l’interface javax. Sql. DataSource.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
