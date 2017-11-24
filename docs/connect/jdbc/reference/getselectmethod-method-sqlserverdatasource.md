---
title: "Méthode getSelectMethod (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.getSelectMethod
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 123c8849983984779940deea46da69ece55de90d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getselectmethod-method-sqlserverdatasource"></a>Méthode getSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le type de curseur par défaut utilisé pour tous les jeux de résultats qui sont créés à l’aide de ce [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** valeur qui contient le type de curseur par défaut.  
  
## <a name="remarks"></a>Notes  
 La propriété selectMethod spécifie le type de curseur par défaut utilisé pour un jeu de résultats. Cette propriété est utile lorsque vous traitez des jeux de résultats volumineux et que vous ne souhaitez pas stocker le jeu de résultats tout entier en mémoire côté client. En définissant la propriété sur « cursor », vous pouvez créer un curseur côté serveur capable d'extraire en une seule fois de plus petits segments de données. Si la propriété selectMethod n'est pas définie, getSelectMethod retourne la valeur par défaut « direct ».  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
