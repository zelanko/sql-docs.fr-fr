---
title: Méthode getObject (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getObject (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a1e955ce-13db-4828-ad59-d9b6a8b2c6cc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e06642390b060164d0e7fba3a8584200e5bc4dd8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981130"
---
# <a name="getobject-method-javalangstring"></a>Méthode getObject (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu'objet dans le langage de programmation Java en fonction du nom du paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.Object getObject(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur **Object**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getObject est spécifiée par la méthode getObject de l’interface java.sql.CallableStatement.  
  
 Cette méthode retourne la valeur de la colonne fournie en tant qu'objet Java. Le type de l'objet Java sera le type d'objet Java par défaut correspondant au type SQL de la colonne, en suivant le mappage pour les types intégrés indiqué dans la spécification JDBC. Si la valeur est SQL NULL, le pilote retourne une valeur Java NULL.  
  
 Cette méthode peut aussi servir à lire des types de données abstraits spécifiques à une base de données. Dans l’API JDBC 2.0, le comportement de la méthode getObject est étendu afin de matérialiser les données des types SQL définis par l’utilisateur. Quand une colonne contient une valeur structurée ou distincte, le comportement de cette méthode s’apparente à celui d’un appel de `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 À compter de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 :  
  
-   Une valeur de type **date** est retournée en tant qu’objet java.sql.Date.  
  
-   Une valeur de type **time** est retournée en tant qu’objet java.sql.Time.  
  
-   Une valeur de type **datetime2** est retournée en tant qu’objet java.sql.Timestamp.  
  
-   Une valeur de type **datetimeoffset** est retournée en tant qu’objet microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>Voir aussi  
 [getObject, méthode (SQLServerCallableStatement)](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
