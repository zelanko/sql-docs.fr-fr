---
description: addBatch, méthode (SQLServerStatement)
title: Méthode addBatch (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.addBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 95924a8b-a43c-4133-aff6-1d712e60e234
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07db37fbc737d5ab83762b6f9b57f09fb09012ac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438281"
---
# <a name="addbatch-method-sqlserverstatement"></a>addBatch, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ajoute la commande SQL donnée à la liste actuelle de commandes de cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 **Chaîne** contenant une instruction SQL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode addBatch est spécifiée par la méthode addBatch de l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
