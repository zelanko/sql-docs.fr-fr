---
title: Méthode getExportedKeys (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getExportedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e89d65955c5637bcd566d48b6e54bcae50397d88
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983304"
---
# <a name="getexportedkeys-method-sqlserverdatabasemetadata"></a>Méthode getExportedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des colonnes de clés étrangères qui référencent les colonnes de clés primaires de la table donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
                                          java.lang.String schema,  
                                          java.lang.String table)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cat*  
  
 **Chaîne** contenant le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le nom du schéma.  
  
 *table*  
  
 **Chaîne** qui contient le nom de la table.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getExportedKeys est spécifiée par la méthode getExportedKeys de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getExportedKeys contient les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**Chaîne**|Nom du catalogue qui contient la table de clés primaires.|  
|PKTABLE_SCHEM|**Chaîne**|Nom du schéma de la table de clés primaires.|  
|PKTABLE_NAME|**Chaîne**|Nom de la table de clés primaires.|  
|PKCOLUMN_NAME|**Chaîne**|Nom de colonne de la clé primaire.|  
|FKTABLE_CAT|**Chaîne**|Nom du catalogue qui contient la table de clés étrangères.|  
|FKTABLE_SCHEM|**Chaîne**|Nom du schéma de la table de clés étrangères.|  
|FKTABLE_NAME|**Chaîne**|Nom de la table de clés étrangères.|  
|FKCOLUMN_NAME|**Chaîne**|Nom de colonne de la clé étrangère.|  
|KEY_SEQ|**short**|Numéro séquentiel de la colonne dans une clé primaire multicolonne.|  
|UPDATE_RULE|**short**|Action appliquée à la clé étrangère lorsque l'opération SQL correspond à une mise à jour. Ce peut être l’une des valeurs suivantes :<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**short**|Action appliquée à la clé étrangère lorsque l'opération SQL correspond à une suppression. Ce peut être l’une des valeurs suivantes :<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**Chaîne**|Nom de la clé étrangère.|  
|PK_NAME|**Chaîne**|Nom de la clé primaire.|  
|DEFERRABILITY|**short**|Indique si l'évaluation de la contrainte de clé étrangère peut être différée jusqu'à une opération de validation. Ce peut être l’une des valeurs suivantes :<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getExportedKeys, consultez « sp_fkeys (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser la méthode getExportedKeys pour retourner des informations sur toutes les clés étrangères qui référencent les clés primaires de la table Person.Contact dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
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
  
  
