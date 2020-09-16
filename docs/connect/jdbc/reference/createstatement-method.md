---
description: Méthode createStatement ()
title: Méthode createStatement () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 480f21b6-50cc-4b1e-a0b0-8774ecfe94f1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f60cca276ffbbf56b09e3ccc297987e45bbf555
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437891"
---
# <a name="createstatement-method-"></a>Méthode createStatement ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) servant à envoyer des instructions SQL à la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Statement createStatement()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet Statement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode createStatement est spécifiée par la méthode createStatement de l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [createStatement, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
