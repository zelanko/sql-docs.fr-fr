---
description: Méthode isSameRM (SQLServerXAResource)
title: Méthode isSameRM (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.isSameRM
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa24c46-b7cf-470a-afa1-52301847a448
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b35a775c8a8ed02dbbb634868e38b1d6c1579a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433411"
---
# <a name="issamerm-method-sqlserverxaresource"></a>Méthode isSameRM (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Détermine si l’instance de gestionnaire de ressources représentée par l’objet cible est identique à celle qui est représentée par l’objet XAResource donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isSameRM(javax.transaction.xa.XAResource xares)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *xares*  
  
 Objet XAResource.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si les instances sont identiques. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Notes  
 Cette méthode commit est spécifiée par la méthode commit de l’interface javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, méthodes](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
