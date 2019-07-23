---
title: Méthode prepareStatement (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c91b965498c0b617a02c7707e369a2ba61c0065
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976157"
---
# <a name="preparestatement-method-javalangstring"></a>Méthode prepareStatement (java.lang.String)

Crée un objet [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) servant à envoyer des instructions SQL paramétrables à la base de données.

## <a name="syntax"></a>Syntaxe

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Paramètres
*sql*

**String** contenant une instruction SQL.

## <a name="return-value"></a>Valeur retournée
Objet PreparedStatement.

## <a name="exceptions"></a>Exceptions  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes
Cette méthode prepareStatement est spécifiée par la méthode prepareStatement dans l’interface java. Sql. Connection.

## <a name="see-also"></a>Voir aussi

[prepareStatement, méthode &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection, membres](./sqlserverconnection-members.md)

[SQLServerConnection, classe](./sqlserverconnection-class.md)
