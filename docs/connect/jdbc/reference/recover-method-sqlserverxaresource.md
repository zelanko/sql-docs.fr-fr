---
title: Méthode recover (SQLServerXAResource) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b78165b8c199a04d716d18614e6fb56232eca429
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923119"
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
  
 Valeur **int** qui peut prendre l'une des valeurs suivantes : XAResource.TMSTARTRSCAN ou XAResource.TMENDRSCAN ou XAResource.TMNOFLAGS ou XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet Xid.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes  
 Cette méthode recover est spécifiée par la méthode recover de l’interface javax.transaction.xa.XAResource.  
  
 Si le paramètre **indicateur** n’est pas XAResource.TMSTARTRSCAN ou XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, une analyse de récupération doit être en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, méthodes](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
