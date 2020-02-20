---
title: Méthode getProcedureColumns (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedureColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0df8fe-3cd6-46e4-ae3c-dc23c35676b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1767519cc2f36bac4a70da84efeb8da9e2a1ec3c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980752"
---
# <a name="getprocedurecolumns-method-sqlserverdatabasemetadata"></a>Méthode getProcedureColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des paramètres de procédure stockée et les colonnes de résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getProcedureColumns(java.lang.String sCatalog,  
                                              java.lang.String sSchema,  
                                              java.lang.String proc,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCatalog*  
  
 **Chaîne** contenant le nom du catalogue. La spécification d'une valeur Null pour ce paramètre indique que le nom du catalogue n'a pas besoin d'être utilisé.  
  
 *sSchema*  
  
 **Chaîne** contenant le modèle de nom du schéma. La spécification d'une valeur Null pour ce paramètre indique que le nom du schéma n'a pas besoin d'être utilisé.  
  
 *proc*  
  
 **Chaîne** contenant le modèle de nom de la procédure.  
  
 *col*  
  
 Valeur **chaîne** qui contient le modèle du nom de la colonne. La spécification d'une valeur Null pour ce paramètre retourne une ligne pour chaque colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getProcedureColumns est spécifiée par la méthode getProcedureColumns de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getProcedureColumns contient les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**Chaîne**|Nom de la base de données qui contient la procédure stockée spécifiée.|  
|PROCEDURE_SCHEM|**Chaîne**|Schéma pour la procédure stockée.|  
|PROCEDURE_NAME|**Chaîne**|Nom de la procédure stockée.|  
|COLUMN_NAME|**Chaîne**|Nom de la colonne.|  
|COLUMN_TYPE|**short**|Type de la colonne. Ce peut être l’une des valeurs suivantes :<br /><br /> procedureColumnUnknown (0)<br /><br /> procedureColumnIn (1)<br /><br /> procedureColumnInOut (2)<br /><br /> procedureColumnOut (4)<br /><br /> procedureColumnReturn (5)<br /><br /> procedureColumnResult (3)|  
|DATA_TYPE|**smallint**|Type de données SQL de java.sql.Types.|  
|TYPE_NAME|**Chaîne**|Nom du type de données.|  
|PRECISION|**int**|Nombre total de chiffres significatifs.|  
|LENGTH|**int**|Longueur des données en octets.|  
|SCALE|**short**|Nombre de chiffres à droite de la virgule décimale.|  
|RADIX|**short**|Base des types numériques.|  
|NULLABLE|**short**|Indique si la colonne peut contenir une valeur Null. Ce peut être l’une des valeurs suivantes :<br /><br /> procedureNoNulls (0)<br /><br /> procedureNullable (1)<br /><br /> procedureNullableUnknown (2)|  
|Remarques|**Chaîne**|Description de la colonne de procédure.<br /><br /> <br /><br /> **Remarque :** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne retourne pas de valeur pour cette colonne.|  
|COLUMN_DEF|**Chaîne**|Valeur par défaut de la colonne.|  
|SQL_DATA_TYPE|**smallint**|Cette colonne est la même que la colonne **DATA_TYPE**, excepté pour les types de données **datetime** et **interval** ISO.|  
|SQL_DATETIME_SUB|**smallint**|Le sous-code **interval** ISO de **datetime** si la valeur de **SQL_DATA_TYPE** est **SQL_DATETIME** ou **SQL_INTERVAL**. Pour les types de données autres que **datetime** et **interval** ISO, cette colonne prend la valeur Null.|  
|CHAR_OCTET_LENGTH|**int**|Nombre maximal d'octets dans la colonne.|  
|ORDINAL_POSITION|**int**|Index de la colonne dans la table.|  
|IS_NULLABLE|**Chaîne**|Indique si la colonne autorise les valeurs Null.|  
|SS_TYPE_CATALOG_NAME|**Chaîne**|Nom du catalogue qui contient le type défini par l'utilisateur (UDT).|  
|SS_TYPE_SCHEMA_NAME|**Chaîne**|Nom du schéma qui contient le type défini par l'utilisateur (UDT).|  
|SS_UDT_CATALOG_NAME|**Chaîne**|Type défini par l'utilisateur (UDT) du nom complet.|  
|SS_UDT_SCHEMA_NAME|**Chaîne**|Nom du catalogue dans lequel un nom de collection de schémas XML est défini. Si le nom du catalogue est introuvable, cette variable contient une chaîne vide.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**Chaîne**|Nom du schéma dans lequel un nom de collection de schémas XML est défini. Si le nom du schéma est introuvable, la chaîne est vide.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**Chaîne**|Nom d'une collection de schémas XML. Si le nom est introuvable, la chaîne est vide.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**Chaîne**|Nom du catalogue qui contient le type défini par l'utilisateur (UDT).|  
|SS_XML_SCHEMACOLLECTION_NAME|**Chaîne**|Nom du schéma qui contient le type défini par l'utilisateur (UDT).|  
|SS_DATA_TYPE|**tinyint**|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisé par les procédures stockées étendues.<br /><br /> <br /><br /> **Remarque :** Pour plus d’informations sur les types de données retournés par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez « Types de données (Transact-SQL) » dans la Documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getProcedureColumns, consultez la rubrique « sp_sproc_columns (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getProcedureColumns pour retourner des informations sur la procédure stockée uspGetBillOfMaterials dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetProcedureColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedureColumns(null, null, "uspGetBillOfMaterials", null);  
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
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
