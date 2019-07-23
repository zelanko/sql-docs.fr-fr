---
title: Méthode Recover (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 92d7b0db997a6b77b43efb6d8104f629bb5507e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976024"
---
# <a name="recover-method-sqlserverxaresource"></a>Méthode recover (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient une liste des branches de transactions préparées à partir d'un gestionnaire de ressources.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *flags*  
  
 Valeur **int** qui peut prendre l’une des valeurs suivantes: XARESOURCE. TMSTARTRSCAN ou XARESOURCE. TMENDRSCAN ou XARESOURCE. TMNOFLAGS ou XARESOURCE. TMSTARTTRSCAN | XAResource. TMENDRSCAN.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet XID.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes  
 Cette méthode recover est spécifiée par la méthode recover de l’interface javax.transaction.xa.XAResource.  
  
 Si l' **indicateur** de paramètre n’est pas XARESOURCE. TMSTARTRSCAN ou XARESOURCE. TMSTARTRSCAN | XAResource. TMENDRSCAN, une analyse de récupération doit être en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, méthodes](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
