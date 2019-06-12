---
title: Méthode getCrossReference (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCrossReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 099dd0bf-b017-479d-9696-f5b06f4c6bf9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2fc70ed3e449840793dbd32e4d2014031256f3bd
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66763004"
---
# <a name="getcrossreference-method-sqlserverdatabasemetadata"></a>Méthode getCrossReference (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des colonnes de clés étrangères dans la table de clés étrangères donnée qui référence les colonnes de clés primaires de la table de clés primaires donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getCrossReference(java.lang.String cat1,  
                                            java.lang.String schem1,  
                                            java.lang.String tab1,  
                                            java.lang.String cat2,  
                                            java.lang.String schem2,  
                                            java.lang.String tab2)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cat1*  
  
 Un **chaîne** qui contient le nom du catalogue de la table qui contient la clé primaire.  
  
 *schem1*  
  
 Un **chaîne** qui contient le nom de schéma de la table qui contient la clé primaire.  
  
 *tab1*  
  
 Un **chaîne** qui contient le nom de la table de la table qui contient la clé primaire.  
  
 *cat2*  
  
 Un **chaîne** qui contient le nom du catalogue de la table qui contient la clé étrangère.  
  
 *schem2*  
  
 Un **chaîne** qui contient le nom de schéma de la table qui contient la clé étrangère.  
  
 *tab2*  
  
 Un **chaîne** qui contient le nom de la table de la table qui contient la clé étrangère.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getCrossReference est spécifiée par la méthode getCrossReference dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getCrossReference contient les informations suivantes :  
  
|Créer une vue d’abonnement|Type|Description|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**String**|Nom du catalogue qui contient la table de clés primaires.|  
|PKTABLE_SCHEM|**String**|Nom du schéma de la table de clés primaires.|  
|PKTABLE_NAME|**String**|Nom de la table de clés primaires.|  
|PKCOLUMN_NAME|**String**|Nom de colonne de la clé primaire.|  
|FKTABLE_CAT|**String**|Nom du catalogue qui contient la table de clés étrangères.|  
|FKTABLE_SCHEM|**String**|Nom du schéma de la table de clés étrangères.|  
|FKTABLE_NAME|**String**|Nom de la table de clés étrangères.|  
|FKCOLUMN_NAME|**String**|Nom de colonne de la clé étrangère.|  
|KEY_SEQ|**short**|Numéro séquentiel de la colonne dans une clé primaire multicolonne.|  
|UPDATE_RULE|**short**|Action appliquée à la clé étrangère lorsque l'opération SQL correspond à une mise à jour. Il peut avoir une des valeurs suivantes :<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**short**|Action appliquée à la clé étrangère lorsque l'opération SQL correspond à une suppression. Il peut avoir une des valeurs suivantes :<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|Nom de la clé étrangère.|  
|PK_NAME|**String**|Nom de la clé primaire.|  
|DEFERRABILITY|**short**|Indique si l'évaluation de la contrainte de clé étrangère peut être différée jusqu'à une opération de validation. Il peut avoir une des valeurs suivantes :<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getCrossReference, consultez « sp_fkeys (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getCrossReference pour retourner des informations sur les relations de clés primaires et étrangères entre les tables Person.Contact et HumanResources.Employee dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetCrossReference(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCrossReference("AdventureWorks", "Person", "Contact", null, "HumanResources", "Employee");  
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
  
  
