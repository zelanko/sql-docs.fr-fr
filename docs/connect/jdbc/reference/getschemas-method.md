---
title: Méthode getSchemas () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSchemas
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: adba0ee6-ff6d-4215-b646-62c735be3fe9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0a5f453e6300258cacffa6606259f85cdd25977
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980078"
---
# <a name="getschemas-method-"></a>Méthode getSchemas ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les noms de schémas disponibles dans la base de données actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getSchemas()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSchemas est spécifiée par la méthode getSchemas de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getSchemas contient les informations suivantes :  
  
|Créer une vue d’abonnement|Type|Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|Nom du schéma.|  
|TABLE_CATALOG|**String**|Nom de catalogue pour le schéma.|  
  
 Les résultats sont classés par TABLE_CATALOG, puis par TABLE_SCHEM. Chaque ligne inclut TABLE_SCHEM comme première colonne et TABLE_CATALOG comme deuxième.  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getSchemas, consultez la rubrique « sys.schemas (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getSchemas pour retourner des informations sur le catalogue et ses noms de schémas associés dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quand l’argument de connexion spécifie la base de données à utiliser.  
  
```  
public static void executeGetSchemas(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getSchemas();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
