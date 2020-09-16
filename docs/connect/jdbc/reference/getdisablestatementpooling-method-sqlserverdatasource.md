---
description: getDisableStatementPooling, méthode (SQLServerDataSource)
title: Méthode getDisableStatementPooling (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 902cceb335ea1f4f5a5858ae3bc80354002ba77b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436221"
---
# <a name="getdisablestatementpooling-method-sqlserverdatasource"></a>getDisableStatementPooling, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de la propriété de connexion **disableStatementPooling**. Ce paramètre contrôle si le regroupement d’instructions est activé ou non pour cette connexion.

  
## <a name="syntax"></a>Syntaxe  
  
```
public boolean getDisableStatementPooling();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Valeur booléenne** qui contient la valeur de la propriété de connexion **disableStatementPooling**.
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible dans la version 6.4 et versions ultérieures du pilote JDBC.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
