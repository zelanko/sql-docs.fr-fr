---
title: Méthode getProcedures (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedures
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 66c9a8b0-dc4c-4cbb-8004-c7157368cab4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f61427cdc3a71ebba5c6d511c3a5c8068b44c496
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47778747"
---
# <a name="getprocedures-method-sqlserverdatabasemetadata"></a>Méthode getProcedures (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des procédures stockées disponibles dans le modèle de nom de catalogue, de schéma ou de procédure stockée donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getProcedures(java.lang.String sCatalog,  
                                        java.lang.String sSchema,  
                                        java.lang.String proc)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCatalog*  
  
 Un **chaîne** qui contient le nom du catalogue. La spécification d'une valeur Null pour ce paramètre indique que le nom du catalogue n'a pas besoin d'être utilisé.  
  
 *%SL*  
  
 **Chaîne** contenant le modèle de nom du schéma. La spécification d'une valeur Null pour ce paramètre indique que le nom du schéma n'a pas besoin d'être utilisé.  
  
 *proc*  
  
 Un **chaîne** qui contient le modèle de nom de procédure.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getProcedures est spécifiée par la méthode getProcedures dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getProcedures contient les informations suivantes :  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**String**|Nom de la base de données qui contient la procédure stockée spécifiée.|  
|PROCEDURE_SCHEM|**String**|Schéma pour la procédure stockée.|  
|PROCEDURE_NAME|**String**|Nom de la procédure stockée.|  
|NUM_INPUT_PARAMS|**Int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_OUTPUT_PARAMS|**Int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_RESULT_SETS|**Int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|REMARKS|**String**|Description de la colonne de procédure.<br /><br /> <br /><br /> **Remarque :** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne retourne pas de valeur pour cette colonne.|  
|PROCEDURE_TYPE|**smallint**|Type de la procédure stockée. Il peut avoir une des valeurs suivantes :<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getProcedures, consultez la rubrique « sp_stored_procedures (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser la méthode getProcedure pour retourner des informations sur la procédure stockée uspGetBillOfMaterials dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetProcedures(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedures(null, null, "uspGetBillOfMaterials");  
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
  
  
