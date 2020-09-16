---
description: Méthode executeUpdate (java.lang.String)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcfb5f6bf2c8697b4463b6726b844bd883e05c19
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437611"
---
# <a name="executeupdate-method-javalangstring"></a>Méthode executeUpdate (java.lang.String)

Exécute l'instruction SQL fournie, qui peut être une instruction INSERT, UPDATE, MERGE ou DELETE ; ou une instruction SQL qui ne retourne rien, telle qu'une instruction SQL DDL.

## <a name="syntax"></a>Syntaxe

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>Paramètres
*sql*

**Chaîne** contenant l’instruction SQL.

## <a name="return-value"></a>Valeur de retour
**int** indiquant le nombre de lignes affectées, ou 0 en cas d’instruction DDL.

## <a name="exceptions"></a>Exceptions
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes
Cette méthode executeUpdate est spécifiée par la méthode executeUpdate de l’interface java.sql.PreparedStatement.

L’appel de cette méthode entraîne une exception, car l’instruction SQL de l’objet SQLServerPreparedStatement est spécifiée lors de la création de l’objet.

## <a name="see-also"></a>Voir aussi

[executeUpdate, méthode &#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[Membres de SQLServerPreparedStatement](./sqlserverpreparedstatement-members.md)

[Classe SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md)
