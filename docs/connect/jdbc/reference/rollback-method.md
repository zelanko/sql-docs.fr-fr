---
title: Rollback, méthode () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.rollback ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7adb6772-4047-4d8e-931d-b3d20eec44b5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e3b4575251cb4eb55f9af37bb81ed2c4bedbf564
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975701"
---
# <a name="rollback-method-"></a>Méthode rollback ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annule toutes les modifications effectuées dans la transaction actuelle et libère tous les verrous de base de données actuellement maintenus par cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void rollback()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rollBack est spécifiée par la méthode rollBack dans l’interface java. Sql. Connection.  
  
 Cette méthode doit être utilisée uniquement lorsque le mode de validation automatique a été désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Rollback, &#40;méthode SQLServerConnection&#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
