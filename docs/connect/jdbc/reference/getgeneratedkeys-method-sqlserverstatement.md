---
description: Méthode getGeneratedKeys (SQLServerStatement)
title: Méthode getGeneratedKeys (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d7b3a4b8ca8f95ab4b62aa1ceee8e330a0b9f9d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435861"
---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>Méthode getGeneratedKeys (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère toutes les clés générées automatiquement du fait de l’exécution de cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet ResultSet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getGeneratedKeys est spécifiée par la méthode getGeneratedKeys de l’interface java.sql.Statement.  
  
 Pour plus d'informations sur l'utilisation de cette méthode, consultez [Utilisation des clés générées](../../../connect/jdbc/using-auto-generated-keys.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
