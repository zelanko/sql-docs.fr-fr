---
title: PrepareStatement, méthode (java.lang.String) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: dbe43cf2af208d6547a1dc3dcd83d7d37947308e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788167"
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
Un objet PreparedStatement.

## <a name="exceptions"></a>Exceptions  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes 
Cette méthode prepareStatement est spécifiée par la méthode prepareStatement dans l’interface java.sql.Connection.

## <a name="see-also"></a> Voir aussi

[prepareStatement, méthode &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection, membres](./sqlserverconnection-members.md)

[SQLServerConnection, classe](./sqlserverconnection-class.md)
