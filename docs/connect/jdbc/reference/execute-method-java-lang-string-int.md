---
title: Execute, méthode (java.lang.String, int[]) | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf42996fac6ac5f48a41311aa072866ebd79f8b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667477"
---
# <a name="execute-method-javalangstring-int"></a>Méthode execute (java.lang.String, int[])

  Exécute l’instruction SQL fournie, qui peut retourner plusieurs résultats, et signale au [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] que les clés générées automatiquement qui sont indiquées dans le tableau spécifié doivent être disponibles pour la récupération.

## <a name="syntax"></a>Syntaxe

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Paramètres
*sql*

Un **chaîne** qui contient une instruction SQL.

*columnIndexes*

Tableau de valeurs **int** indiquant les index de colonne des clés générées automatiquement qui doivent être disponibles.

## <a name="return-value"></a>Valeur retournée
**true** si le premier résultat est un jeu de résultats. Dans le cas contraire, la valeur est **false**.
  
## <a name="exceptions"></a>Exceptions
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes 
Cette méthode execute est spécifiée par la méthode execute dans l’interface java.sql.Statement.

## <a name="see-also"></a> Voir aussi

[exécuter la méthode &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement, membres](./sqlserverstatement-members.md)

[SQLServerStatement, classe](./sqlserverstatement-class.md)
