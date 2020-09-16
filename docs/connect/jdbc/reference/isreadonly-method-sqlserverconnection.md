---
description: Méthode isReadOnly (SQLServerConnection)
title: Méthode isReadOnly (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isReadOnly
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 902fd2c1-05e0-436e-9779-c048cdb8475a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44a3255f8743384a8807388b7d2f0f8692fa61a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433441"
---
# <a name="isreadonly-method-sqlserverconnection"></a>Méthode isReadOnly (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) est en mode lecture seule.  
  
> [!NOTE]  
>  Actuellement, cette méthode n’est pas prise en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isReadOnly()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la connexion est en mode lecture seule, **false** si ce n’est pas le cas.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isReadOnly est spécifiée par la méthode isReadOnly de l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
