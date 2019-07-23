---
title: Méthode executeUpdate (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 04b3bdcd2b495513500d07583fadc910fe9c13a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954683"
---
# <a name="executeupdate-method-javalangstring"></a>Méthode executeUpdate (java.lang.String)

Exécute l'instruction SQL fournie, qui peut être une instruction INSERT, UPDATE, MERGE ou DELETE ; ou une instruction SQL qui ne retourne rien, telle qu'une instruction SQL DDL.

## <a name="syntax"></a>Syntaxe

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>Paramètres
*sql*

**Chaîne** qui contient l’instruction SQL.

## <a name="return-value"></a>Valeur retournée
**Entier** qui indique le nombre de lignes affectées, ou 0 si vous utilisez une instruction DDL.

## <a name="exceptions"></a>Exceptions
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes
Cette méthode executeUpdate est spécifiée par la méthode executeUpdate de l’interface java.sql.PreparedStatement.

L’appel de cette méthode entraîne une exception, car l’instruction SQL de l’objet SQLServerPreparedStatement est spécifiée lors de la création de l’objet.

## <a name="see-also"></a>Voir aussi

[executeUpdate, méthode &#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[SQLServerPreparedStatement, membres](./sqlserverpreparedstatement-members.md)

[SQLServerPreparedStatement, classe](./sqlserverpreparedstatement-class.md)
