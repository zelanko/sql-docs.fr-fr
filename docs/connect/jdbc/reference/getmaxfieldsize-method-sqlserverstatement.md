---
description: getMaxFieldSize, méthode (SQLServerStatement)
title: Méthode getMaxFieldSize (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0930c5ab4b3c2e907a6de9caeef96f78d57e2737
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435561"
---
# <a name="getmaxfieldsize-method-sqlserverstatement"></a>getMaxFieldSize, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal d’octets pouvant être retournés pour des valeurs de colonne de caractères ou binaire dans un objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) produit par cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre maximal d’octets qu’une colonne peut contenir, ou 0 s’il n’y a pas de limite.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxFieldSize est spécifiée par la méthode getMaxFieldSize de l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, méthodes](../../../connect/jdbc/reference/sqlserverstatement-methods.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
