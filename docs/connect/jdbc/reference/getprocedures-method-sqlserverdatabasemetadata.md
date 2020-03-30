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
ms.openlocfilehash: 054ce4f6f646f873d4aff05fbe1d31aa9903ded9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67980738"
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
  
 **Chaîne** contenant le nom du catalogue. La spécification d'une valeur Null pour ce paramètre indique que le nom du catalogue n'a pas besoin d'être utilisé.  
  
 *sSchema*  
  
 **Chaîne** contenant le modèle de nom du schéma. La spécification d'une valeur Null pour ce paramètre indique que le nom du schéma n'a pas besoin d'être utilisé.  
  
 *proc*  
  
 **Chaîne** contenant le modèle de nom de la procédure.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getProcedures est spécifiée par la méthode getProcedures de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getProcedures contient les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**Chaîne**|Nom de la base de données qui contient la procédure stockée spécifiée.|  
|PROCEDURE_SCHEM|**Chaîne**|Schéma pour la procédure stockée.|  
|PROCEDURE_NAME|**Chaîne**|Nom de la procédure stockée.|  
|NUM_INPUT_PARAMS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_OUTPUT_PARAMS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|NUM_RESULT_SETS|**int**|Réservé pour un usage ultérieur, retourne actuellement la valeur -1.|  
|Remarques|**Chaîne**|Description de la colonne de procédure.<br /><br /> <br /><br /> **Remarque :** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne retourne pas de valeur pour cette colonne.|  
|PROCEDURE_TYPE|**smallint**|Type de la procédure stockée. Ce peut être l’une des valeurs suivantes :<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getProcedures, consultez la rubrique « sp_stored_procedures (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
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
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
