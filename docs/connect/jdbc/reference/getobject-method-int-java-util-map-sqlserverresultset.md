---
description: Méthode getObject (int, java.util.Map) (SQLServerResultSet)
title: getObject, méthode (int, java.util.Map) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getObject (int, java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df85a514-ab43-4bf6-98dd-f7f37fad1850
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab41981f6140dc0c197f66c2cf7fcb7133e7ad29
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435191"
---
# <a name="getobject-method-int-javautilmap-sqlserverresultset"></a>Méthode getObject (int, java.util.Map) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient la valeur de l’index de la colonne désignée dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant qu’objet dans le langage de programmation Java, en utilisant l’objet Map donné.  
  
> [!NOTE]  
>  Actuellement, cette méthode n’est pas prise en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Lorsqu'elle est utilisée, cette méthode retourne toujours le mappage par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.Object getObject(int i,  
                                  java.util.Map map)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *i*  
  
 **int** indiquant l’index de la colonne.  
  
 *map*  
  
 Objet Map.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur **Object**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getObject est spécifiée par la méthode getObject de l’interfacejava.sql.ResultSet.  
  
 Cette méthode retourne la valeur de la colonne fournie en tant qu'objet Java. Le type de l'objet Java sera le type d'objet Java par défaut correspondant au type SQL de la colonne, en suivant le mappage pour les types intégrés indiqué dans la spécification JDBC. Si la valeur est SQL NULL, le pilote retourne une valeur Java NULL.  
  
 Cette méthode peut aussi servir à lire des types de données abstraits spécifiques à une base de données. Dans l’API JDBC 2.0, le comportement de la méthode getObject est étendu afin de matérialiser les données des types SQL définis par l’utilisateur. Quand une colonne contient une valeur structurée ou distincte, le comportement de cette méthode s’apparente à celui d’un appel de `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 À compter de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 :  
  
-   Une valeur de type date est retournée en tant qu'objet java.sql.Date.  
  
-   Une valeur de type time est retournée en tant qu'objet java.sql.Time.  
  
-   Une valeur de type datetime2 est retournée en tant qu'objet java.sql.Timestamp.  
  
-   Une valeur de type datetimeoffset est retournée en tant qu'objet microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>Voir aussi  
 [getObject, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
