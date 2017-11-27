---
title: "Méthode executeUpdate (java.lang.String) | Documents Microsoft"
ms.custom: 
ms.date: 02/07/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a78fe10c14c54b5e2bea1cc4030a4f5d8d83fa1
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="executeupdate-method-javalangstring"></a>Méthode executeUpdate (java.lang.String)

Exécute l'instruction SQL fournie, qui peut être une instruction INSERT, UPDATE, MERGE ou DELETE ; ou une instruction SQL qui ne retourne rien, telle qu'une instruction SQL DDL.

## <a name="syntax"></a>Syntaxe

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>Paramètres
*SQL*

A **chaîne** qui contient l’instruction SQL.

## <a name="return-value"></a>Valeur retournée
Un **int** qui indique le nombre de lignes affectées ou 0 si vous utilisez une instruction DDL.

## <a name="exceptions"></a>Exceptions
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes
Cette méthode executeUpdate est spécifiée par la méthode executeUpdate dans l’interface java.sql.PreparedStatement.

Appel de cette méthode entraîne une exception, car l’instruction SQL pour l’objet SQLServerPreparedStatement est spécifiée lorsque l’objet est créé.

## <a name="see-also"></a>Voir aussi

[Méthode executeUpdate &#40; SQLServerPreparedStatement &#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[SQLServerPreparedStatement, membres](./sqlserverpreparedstatement-members.md)

[SQLServerPreparedStatement, classe](./sqlserverpreparedstatement-class.md)
