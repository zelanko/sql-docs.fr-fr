---
title: Méthode execute (java.lang.String, int[]) | Microsoft Docs
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
ms.openlocfilehash: 6e96e0c9c957522db6a766b3491d394b7337d7b6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954983"
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

**Chaîne** contenant une instruction SQL.

*columnIndexes*

Tableau de valeurs **int** indiquant les index de colonne des clés générées automatiquement qui doivent être disponibles.

## <a name="return-value"></a>Valeur de retour
**true** si le premier résultat est un jeu de résultats. Dans le cas contraire, la valeur est **false**.
  
## <a name="exceptions"></a>Exceptions
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes 
Cette méthode execute est spécifiée par la méthode execute de l’interface java.sql.Statement.

## <a name="see-also"></a> Voir aussi

[Méthode execute &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement, membres](./sqlserverstatement-members.md)

[SQLServerStatement, classe](./sqlserverstatement-class.md)
