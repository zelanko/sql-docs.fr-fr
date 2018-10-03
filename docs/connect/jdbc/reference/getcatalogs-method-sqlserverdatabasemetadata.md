---
title: Méthode getCatalogs (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e81c905a483972ab0dfe7b03573bc30bf6d474e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727187"
---
# <a name="getcatalogs-method-sqlserverdatabasemetadata"></a>Méthode getCatalogs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les noms de catalogues disponibles sur le serveur connecté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getCatalogs est spécifiée par la méthode getCatalogs dans l’interface java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  Sur SQL Azure, vous devez vous connecter à la base de données master pour appeler **SQLServerDatabaseMetaData.getCatalogs**. SQL Azure ne prend pas en charge le retour de l’ensemble complet des catalogues d’une base de données utilisateur. **SQLServerDatabaseMetaData.getCatalogs** utilise la vue sys.databases pour obtenir les catalogues. Reportez-vous à la section autorisations dans [sys.databases (base de données SQL Azure)](http://go.microsoft.com/fwlink/?LinkId=217396) pour comprendre **SQLServerDatabaseMetaData.getCatalogs** comportement sur SQL Azure.  
  
 Le jeu de résultats retourné par la méthode getCatalogs contient les informations suivantes :  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nom du catalogue, avec les bases de données système dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser la méthode getCatalogs pour retourner le nom de toutes les bases de données contenues dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], avec les bases de données système.  
  
```  
public static void executeGetCatalogs(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCatalogs();  
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
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
