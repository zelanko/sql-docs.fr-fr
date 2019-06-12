---
title: setpoolable, méthode (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c63c526aed7bfae6027f3a9aa028bc2a2e20fbef
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799646"
---
# <a name="setpoolable-method-sqlserverstatement"></a>setPoolable, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Demande qu'une instruction soit regroupée ou non.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Paramètres  
 *poolable*  
  
 Si la valeur est **true**, demande à ce que l’instruction soit regroupée. Si la valeur est **false**, demande à ce que l’instruction ne soit pas regroupée.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 La valeur spécifiée dans le paramètre *poolable* constitue une indication d’implémentation qui spécifie si l’application souhaite que l’instruction soit regroupée. Le gestionnaire de regroupement d'instructions décide s'il va utiliser cette indication.  
  
 La valeur de regroupement d'une instruction s'applique à la fois aux caches d'instructions internes implémentés par le pilote et aux caches d'instructions externes implémentés par des serveurs d'applications et d'autres applications.  
  
 Par défaut, un objet SQLServerStatement n’est pas regroupé. Objets SQLServerPreparedStatement et SQLServerCallableStatement sont à leur création.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) est levée si cette méthode est appelée sur une instruction fermée.  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) retourne une valeur indiquant si l’objet est regroupé.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
