---
description: isPoolable, méthode (SQLServerStatement)
title: Méthode isPoolable (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1b8b3e817ddaf2983d1cfec64099c220e012e16
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433481"
---
# <a name="ispoolable-method-sqlserverstatement"></a>isPoolable, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur qui indique s'il est possible d'ajouter une instruction au regroupement d'instructions fourni par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isPoolable() throws SQLException  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si l’instruction peut être ajoutée au regroupement d’instructions fourni par l’utilisateur ; **false** sinon.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md) modifie le comportement (regroupable/non regroupable) d’un objet.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
