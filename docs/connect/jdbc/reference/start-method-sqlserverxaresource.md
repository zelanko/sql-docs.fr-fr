---
title: Méthode start (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.start
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 33c90213-92f7-416b-b2fa-67a1afe64e97
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cef1af2c416231892ea74a7def90237f84b036d8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67970034"
---
# <a name="start-method-sqlserverxaresource"></a>Méthode start (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Commence le travail pour le compte d’une branche de transaction spécifiée dans l’objet Xid.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void start(javax.transaction.xa.Xid xid,  
                  int flags)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *xid*  
  
 Objet Xid.  
  
 *flags*  
  
 Valeur **int**.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes  
 Cette méthode start est spécifiée par la méthode start de l’interface javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, méthodes](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
