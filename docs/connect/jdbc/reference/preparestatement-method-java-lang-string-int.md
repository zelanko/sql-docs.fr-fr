---
title: Méthode prepareStatement (java.lang.String) | Documents Microsoft
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
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26f242db545a79e27ba72808e6c6ce466dbe5f40
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="preparestatement-method-javalangstring"></a>Méthode prepareStatement (java.lang.String)

Crée un [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) objet pour envoyer des instructions SQL paramétrées à la base de données.

## <a name="syntax"></a>Syntaxe

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Paramètres
*sql*

A **chaîne** contenant une instruction SQL.

## <a name="return-value"></a>Valeur retournée
Un objet PreparedStatement.

## <a name="exceptions"></a>Exceptions  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Notes
Cette méthode prepareStatement est spécifiée par la méthode prepareStatement dans l’interface java.sql.Connection.

## <a name="see-also"></a>Voir aussi

[Méthode prepareStatement &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection, membres](./sqlserverconnection-members.md)

[SQLServerConnection, classe](./sqlserverconnection-class.md)
