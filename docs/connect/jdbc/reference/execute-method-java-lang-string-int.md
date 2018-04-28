---
title: Méthode Execute (java.lang.String, int[]) | Documents Microsoft
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86e02aa3ec56deffefe81ad5ebe4d282ecd10d53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="execute-method-javalangstring-int"></a>Méthode execute (java.lang.String, int[])

  Exécute l’instruction SQL fournie, qui peut retourner plusieurs résultats et les signaux [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion-md.md)] que les clés générées automatiquement qui sont indiquées dans le tableau spécifié doivent être accessibles pour la récupération.

## <a name="syntax"></a>Syntaxe

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Paramètres
*sql*

A **chaîne** qui contient une instruction SQL.

*columnIndexes*

Un tableau de **int**qui indique l’index de colonne des clés générées automatiquement qui doivent être disponibles.

## <a name="return-value"></a>Valeur retournée
**true** si le premier résultat est un jeu de résultats. Dans le cas contraire, la valeur est **false**.
  
## <a name="exceptions"></a>Exceptions
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes
Cette méthode execute est spécifiée par la méthode d’exécution dans l’interface java.sql.Statement.

## <a name="see-also"></a>Voir aussi

[exécuter la méthode &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[Membres de SQLServerStatement](./sqlserverstatement-members.md)

[Classe SQLServerStatement](./sqlserverstatement-class.md)
