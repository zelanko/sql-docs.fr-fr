---
title: Méthode setTransactionTimeout (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.setTransactionTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38bf4a1a-6ad3-437c-b9ed-8792ab6dde7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81bf280397b2ba1ddac428eb12c882af2b31e1b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47615507"
---
# <a name="settransactiontimeout-method-sqlserverxaresource"></a>Méthode setTransactionTimeout (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la valeur du délai d’expiration actuel des transactions de cet objet [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean setTransactionTimeout(int seconds)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *secondes*  
  
 Un **int** valeur.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si le délai d’attente a été défini correctement. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes   
 Cette méthode setTransactionTimeout est spécifiée par la méthode setTransactionTimeout dans l’interface javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerXAResource, méthodes](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
