---
title: Méthode getColumns (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f173fa5d-e114-4a37-a5c4-2baad9ff3af1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d34f5748a5a85d67754ea9a001ba1819935e53a6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67952839"
---
# <a name="getcolumns-method-sqlserverdatabasemetadata"></a>Méthode getColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des colonnes d'une table qui sont disponibles dans le catalogue spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getColumns(java.lang.String catalog,  
                                     java.lang.String schema,  
                                     java.lang.String table,  
                                     java.lang.String col)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 **Chaîne** contenant le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le modèle de nom du schéma.  
  
 *table*  
  
 **String** contenant le modèle de nom de la table.  
  
 *col*  
  
 Valeur **chaîne** qui contient le modèle du nom de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumns est spécifiée par la méthode getColumns de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getColumns contient les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Chaîne**|Nom du catalogue.|  
|TABLE_SCHEM|**Chaîne**|Le nom du schéma de la table.|  
|TABLE_NAME|**Chaîne**|Nom de la table.|  
|COLUMN_NAME|**Chaîne**|Nom de la colonne.|  
|DATA_TYPE|**smallint**|Type de données SQL de java.sql.Types.|  
|TYPE_NAME|**Chaîne**|Nom du type de données.|  
|COLUMN_SIZE|**int**|Précision de la colonne.|  
|BUFFER_LENGTH|**smallint**|Taille de transfert des données.|  
|DECIMAL_DIGITS|**smallint**|Échelle de la colonne.|  
|NUM_PREC_RADIX|**smallint**|Base de la colonne.|  
|NULLABLE|**smallint**|Indique si la colonne accepte la valeur Null. Ce peut être l’une des valeurs suivantes :<br /><br /> columnNoNulls (0)<br /><br /> columnNullable (1)|  
|Remarques|**Chaîne**|Commentaires associés à la colonne.<br /><br /> **Remarque :**  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retourne toujours Null pour cette colonne.|  
|COLUMN_DEF|**Chaîne**|Valeur par défaut de la colonne.|  
|SQL_DATA_TYPE|**smallint**|Valeur du type de données SQL tel qu'il apparaît dans le champ TYPE du descripteur. Cette colonne est la même que la colonne DATA_TYPE, excepté pour le type de données datetime et pour le type de données interval de SQL-92. Cette colonne renvoie toujours une valeur.|  
|SQL_DATETIME_SUB|**smallint**|Code de sous-type pour le type de données datetime et pour le type de données interval de SQL-92. Pour les autres types de données, cette colonne renvoie la valeur NULL.|  
|CHAR_OCTET_LENGTH|**int**|Nombre maximal d'octets dans la colonne.|  
|ORDINAL_POSITION|**int**|Index de la colonne dans la table.|  
|IS_NULLABLE|**Chaîne**|Indique si la colonne autorise les valeurs Null.|  
|SS_IS_SPARSE|**smallint**|Si la colonne est une colonne éparse, la valeur est 1 ; sinon, 0.<sup>1</sup>|  
|SS_IS_COLUMN_SET|**smallint**|Si la colonne est la colonne éparse column_set, la valeur est 1 ; sinon, 0. <sup>1</sup>|  
|SS_IS_COMPUTED|**smallint**|Indique si une colonne dans un TABLE_TYPE est une colonne calculée. <sup>1</sup>|  
|IS_AUTOINCREMENT|**Chaîne**|« YES » si la colonne est incrémentée automatiquement. « NO » si la colonne n'est pas incrémentée automatiquement. « » (chaîne vide) si le pilote ne peut pas déterminer si la colonne est incrémentée automatiquement. <sup>1</sup>|  
|SS_UDT_CATALOG_NAME|**Chaîne**|Nom du catalogue qui contient le type défini par l'utilisateur (UDT). <sup>1</sup>|  
|SS_UDT_SCHEMA_NAME|**Chaîne**|Nom du schéma qui contient le type défini par l'utilisateur (UDT). <sup>1</sup>|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**Chaîne**|Type défini par l'utilisateur (UDT) du nom complet. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**Chaîne**|Nom du catalogue dans lequel un nom de collection de schémas XML est défini. Si le nom du catalogue est introuvable, cette variable contient une chaîne vide. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**Chaîne**|Nom du schéma dans lequel un nom de collection de schémas XML est défini. Si le nom du schéma est introuvable, la chaîne est vide. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_NAME|**Chaîne**|Nom d'une collection de schémas XML. Si le nom est introuvable, la chaîne est vide. <sup>1</sup>|  
|SS_DATA_TYPE|**tinyint**|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisé par les procédures stockées étendues.<br /><br /> **Remarque** : Pour plus d’informations sur les types de données retournés par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez la rubrique « Types de données (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
 (1) Cette colonne sera absente si vous vous connectez à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getColumns, consultez la rubrique « sp_columns (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0, vous constaterez les modifications de comportement suivantes par rapport aux versions antérieures du pilote JDBC :  
  
 La colonne DATA_TYPE intègre les modifications suivantes :  
  
|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Type de retour dans le pilote JDBC version 2.0 (ou en cas de connexion à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]) et constante numérique associée|Type de retour dans le pilote JDBC version 3.0 en cas de connexion à [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)] ou ultérieur|  
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|  
|type défini par l'utilisateur supérieur à 8 Ko|LONGVARBINARY (-4)|VARBINARY (-3)|  
|Geography|LONGVARBINARY (-4)|VARBINARY (-3)|  
|geometry|LONGVARBINARY (-4)|VARBINARY (-3)|  
|varbinary(max)|LONGVARBINARY (-4)|VARBINARY (-3)|  
|nvarchar(max)|LONGVARCHAR (-1) ou LONGNVARCHAR (JDBC 4) (-16)|VARCHAR (12) ou NVARCHAR (JDBC 4) (-9)|  
|varchar(max)|LONGVARCHAR (-1)|VARCHAR (12)|  
|time|VARCHAR (12) ou NVARCHAR (JDBC 4) (-9)|TIME (-154)|  
|Date|VARCHAR (12) ou NVARCHAR (JDBC 4) (-9)|DATE (91)|  
|datetime2|VARCHAR (12) ou NVARCHAR (JDBC 4) (-9)|TIMESTAMP (93)|  
|datetimeoffset|VARCHAR (12) ou NVARCHAR (JDBC 4) (-9)|microsoft.sql.Types.DATETIMEOFFSET  (-155)|  
  
 La colonne COLUMN_SIZE intègre les modifications suivantes :  
  
|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Type de retour dans le pilote JDBC version 2.0|Type de retour dans le pilote JDBC version 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|nvarchar(max)|1073741823|2147483647 (métadonnées de base de données)|  
|Xml|1073741823|2147483647 (métadonnées de base de données)|  
|type défini par l'utilisateur inférieur ou égal à 8 Ko|8 Ko (jeu de résultats et métadonnées de paramètre)|Taille réelle retournée par la procédure stockée.|  
|time||Longueur en caractères de la représentation de chaîne du type, en tenant compte de la précision maximale autorisée pour le composant fractions de seconde.|  
|Date||identique à time|  
|datetime2||identique à time|  
|datetimeoffset||identique à time|  
  
 La colonne BUFFER_LENGTH intègre la modification suivante :  
  
|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Type de retour dans le pilote JDBC version 2.0|Type de retour dans le pilote JDBC version 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|type défini par l'utilisateur supérieur à 8 Ko||2147483647|  
  
 La colonne TYPE_NAME intègre les modifications suivantes :  
  
|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Type de retour dans le pilote JDBC version 2.0|Type de retour dans le pilote JDBC version 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|varchar(max)|text|varchar|  
|varbinary(max)|image|varbinary|  
  
 La colonne DECIMAL_DIGITS intègre les modifications suivantes :  
  
|Type [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Pilote JDBC version 2.0|Pilote JDBC version 3.0|  
|--------------------------------------------------------------|---------------------|---------------------|  
|time|null|7 (ou inférieur, si spécifié)|  
|Date|null|null|  
|datetime2|null|7 (ou inférieur, si spécifié)|  
|datetimeoffset|null|7 (ou inférieur, si spécifié)|  
  
 La colonne SQL_DATA_TYPE intègre les modifications suivantes :  
  
|Type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Valeur des données de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2008 dans le pilote JDBC version 2.0|Valeur des données de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2008 dans le pilote JDBC version 3.0|  
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|varchar(max)|-10|-9|  
|nvarchar(max)|-1|-9|  
|Xml|-10|-152|  
|type défini par l'utilisateur inférieur ou égal à 8 Ko|-3|-151|  
|type défini par l'utilisateur supérieur à 8 Ko|Non disponible dans le pilote JDBC version 2.0|-151|  
|Geography|-4|-151|  
|geometry|-4|-151|  
|hierarchyid|-4|-151|  
|time|-9|92|  
|Date|-9|91|  
|datetime2|-9|93|  
|datetimeoffset|-9|-155|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getColumns pour retourner des informations pour la table Person.Contact dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
import java.sql.*;  
public class c1 {  
   public static void main(String[] args) {  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedsecurity=true";  
  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
         DatabaseMetaData dbmd = con.getMetaData();  
         rs = dbmd.getColumns("AdventureWorks", "Person", "Contact", "FirstName");  
  
         ResultSet r = dbmd.getColumns(null, null, "Contact", null);  
         ResultSetMetaData rm = r.getMetaData();   
         int noofcols = rm.getColumnCount();  
  
         if (r.next())  
            for (int i = 0 ; i < noofcols ; i++ )  
            System.out.println(rm.getColumnName( i + 1 ) + ": \t\t" + r.getString( i + 1 ));  
      }  
  
      catch (Exception e) {}  
      finally {}  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
