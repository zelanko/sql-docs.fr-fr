---
description: Méthode getLoginTimeout (SQLServerDataSource)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d1a868a7fc9f562496037dd4280de91aac28b335
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435731"
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>Méthode getLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nombre de secondes pendant lesquelles cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) patiente lors de la tentative de connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur **int** représentant le nombre de secondes à attendre.  
  
## <a name="remarks"></a>Notes  
 Si l'application ne spécifie pas explicitement une valeur de délai d'attente, cette méthode retourne une valeur par défaut de 15 secondes.  
  
 Cette méthode getLoginTimeout est spécifiée par la méthode getLoginTimeout de l’interface javax.sql.DataSource.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
