---
description: Méthode setSelectMethod (SQLServerDataSource)
title: Méthode setSelectMethod (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c2b9c0fb4fb5f2a410abc790bf2f40d2bd2a64e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458362"
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>Méthode setSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le type de curseur par défaut utilisé pour tous les jeux de résultats créés à l’aide de cet objet [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *selectMethod*  
  
 Valeur **String** contenant le type de curseur par défaut.  
  
## <a name="remarks"></a>Notes  
 La méthode selectMethod correspond au type de curseur par défaut qui est utilisé pour un jeu de résultats. Cette propriété est utile lorsque vous travaillez avec des jeux de résultats volumineux et ne souhaitez pas stocker l'ensemble du jeu de résultats en mémoire côté client. En définissant la propriété sur « cursor », vous pouvez créer un curseur côté serveur capable d'extraire en une seule fois de plus petits segments de données. Si la propriété selectMethod n’est pas définie, [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) retourne la valeur par défaut (« direct »).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
