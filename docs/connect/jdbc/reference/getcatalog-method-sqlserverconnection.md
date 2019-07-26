---
title: Méthode getCatalog (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e87ef65f-4b5a-4e1c-8db5-7f0932390bb0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a0f6d74b8dee21333c1358a9f998371e38b5c0cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953344"
---
# <a name="getcatalog-method-sqlserverconnection"></a>getCatalog, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nom de catalogue actuel de cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getCatalog()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **Chaîne** qui contient le nom du catalogue.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getCatalog, est spécifiée par la méthode getCatalog, dans l’interface java. Sql. Connection.  
  
 Retourne la propriété de catalogue actuelle de l’objet SQLServerConnection, ou null si elle n’est pas définie. La propriété catalog est définie explicitement avec la méthode [setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md), ou mise à jour implicitement en lisant le changement d’environnement sur TDS pour le catalogue actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
