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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b17c514a293f4566c3408e364acccbab721e1ce
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923141"
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

## <a name="return-value"></a>Valeur de retour
Objet PreparedStatement.

## <a name="exceptions"></a>Exceptions  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes
Cette méthode prepareStatement est spécifiée par la méthode prepareStatement de l’interface java.sql.Connection.

## <a name="see-also"></a>Voir aussi

[prepareStatement, méthode &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection, membres](./sqlserverconnection-members.md)

[SQLServerConnection, classe](./sqlserverconnection-class.md)
