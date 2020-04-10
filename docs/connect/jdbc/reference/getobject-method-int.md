---
title: Méthode getObject (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getObject (jnt)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4b8366b-c065-48e1-b712-19e2d9834228
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d20134de6b7df5d444da12b03de9a938c3bd13bd
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80904937"
---
# <a name="getobject-method-int"></a>Méthode getObject (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu'objet dans le langage de programmation Java en fonction de l'index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.Object getObject(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 **int** indiquant l’index du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur **Object**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getObject est spécifiée par la méthode getObject de l’interface java.sql.CallableStatement.  
  
 Cette méthode retourne la valeur de la colonne fournie en tant qu'objet Java. Le type de l'objet Java sera le type d'objet Java par défaut correspondant au type SQL de la colonne, en suivant le mappage pour les types intégrés indiqué dans la spécification JDBC. Si la valeur est SQL NULL, le pilote retourne une valeur Java NULL.  
  
 Cette méthode peut aussi servir à lire des types de données abstraits spécifiques à une base de données. Dans JDBC 2.0, le comportement de la méthode getObject a été étendu afin de matérialiser les données des types SQL définis par l’utilisateur. Quand une colonne contient une valeur structurée ou distincte, le comportement de cette méthode s’apparente à celui d’un appel de `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 À compter de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 :  
  
-   Une valeur de type **date** est retournée en tant qu’objet java.sql.Date.  
  
-   Une valeur de type **time** est retournée en tant qu’objet java.sql.Time.  
  
-   Une valeur de type **datetime2** est retournée en tant qu’objet java.sql.Timestamp.  
  
-   Une valeur de type **datetimeoffset** est retournée en tant qu’objet microsoft.sql.DateTimeOffset.  
  
## <a name="see-also"></a>Voir aussi  
 [getObject, méthode (SQLServerCallableStatement)](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
