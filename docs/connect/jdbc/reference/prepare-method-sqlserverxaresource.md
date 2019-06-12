---
title: Méthode Prepare (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.prepare
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f800c966-3fae-41b3-963a-464988f80da3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: acf6efd0799b129ed06ab272a67e5bf6bebfb05c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66771026"
---
# <a name="prepare-method-sqlserverxaresource"></a>Méthode prepare (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Demande au gestionnaire de ressources de se préparer à une validation de la transaction spécifiée par l’objet Xid donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int prepare(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *xid*  
  
 Un objet Xid.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes  
 Cette méthode prepare est spécifiée par la méthode prepare de l’interface javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, méthodes](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
