---
title: "getSchemas (méthode) (String, String) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 24176593bf253b1a5482ac5df74a558046148c96
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getschemas-method-string-string"></a>Méthode getSchemas (String, String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les noms de schémas disponibles dans la base de données actuelle à l'aide du nom de catalogue spécifié et du nom de schéma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public ResultSet getSchemas(java.lang.String catalog,  
                       java.lang.String schemaPattern)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalogue*  
  
 Nom d'un catalogue dans la base de données. Si la chaîne est vide « », le résultat inclut les schémas sans catalogue. S’il s’agit **null**, le nom du catalogue n’est pas utilisé pour la recherche.  
  
 *schemaPattern*  
  
 Nom d'un schéma. S’il s’agit **null**, le nom de schéma n’est pas utilisé pour la recherche.  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSchemas est spécifiée par la méthode getSchemas dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getSchemas contient les informations suivantes :  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**Chaîne**|Le nom du schéma.|  
|TABLE_CATALOG|**Chaîne**|Nom de catalogue pour le schéma.|  
  
 Les résultats sont classés par TABLE_CATALOG, puis par TABLE_SCHEM. Chaque ligne inclut TABLE_SCHEM comme première colonne et TABLE_CATALOG comme deuxième.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

