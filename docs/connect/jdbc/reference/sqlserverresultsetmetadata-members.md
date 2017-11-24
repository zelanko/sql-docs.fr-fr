---
title: Membres de SQLServerResultSetMetaData | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37587981-2979-49a3-a6ab-df4bfb9b8748
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: df2f0fbfe57b258bf0ad314377f0d11925ac03b9
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverresultsetmetadata-members"></a>Membres de SQLServerResultSetMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Les tableaux suivants répertorient les membres qui sont exposées par le [SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) classe.  
  
## <a name="constructors"></a>Constructeurs  
 Aucun.  
  
## <a name="fields"></a>Champs  
 Aucun.  
  
## <a name="inherited-fields"></a>Champs hérités  
  
|Nom| Description|  
|----------|-----------------|  
|java.sql.ResultSetMetaData|columnNoNulls, columnNullable, columnNullableUnknown|  
  
## <a name="methods"></a>Méthodes  
  
|Nom| Description|  
|----------|-----------------|  
|[getCatalogName](../../../connect/jdbc/reference/getcatalogname-method-sqlserverresultsetmetadata.md)|Obtient le nom de catalogue pour la table qui inclut la colonne désignée.|  
|[getColumnClassName](../../../connect/jdbc/reference/getcolumnclassname-method-sqlserverresultsetmetadata.md)|Retourne le nom qualifié complet de la classe Java dont les instances sont créées si la [getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md) méthode de la [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) classe est appelé pour extraire une valeur de la colonne.|  
|[getColumnCount](../../../connect/jdbc/reference/getcolumncount-method-sqlserverresultsetmetadata.md)|Retourne le nombre de colonnes dans le jeu de résultats.|  
|[getColumnDisplaySize](../../../connect/jdbc/reference/getcolumndisplaysize-method-sqlserverresultsetmetadata.md)|Retourne la largeur maximale normale, en caractères, de la colonne désignée.|  
|[getColumnLabel](../../../connect/jdbc/reference/getcolumnlabel-method-sqlserverresultsetmetadata.md)|Obtient le titre suggéré à utiliser dans les impressions et les affichages de la colonne désignée.|  
|[getColumnName](../../../connect/jdbc/reference/getcolumnname-method-sqlserverresultsetmetadata.md)|Obtenir le nom de la colonne désignée.|  
|[getColumnType](../../../connect/jdbc/reference/getcolumntype-method-sqlserverresultsetmetadata.md)|Récupère le type SQL de la colonne désignée.|  
|[getColumnTypeName](../../../connect/jdbc/reference/getcolumntypename-method-sqlserverresultsetmetadata.md)|Récupère le nom de type spécifique à la base de données de la colonne désignée.|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverresultsetmetadata.md)|Obtient le nombre de décimales pour la colonne désignée.|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverresultsetmetadata.md)|Obtient le nombre de chiffres à droite de la virgule décimale pour la colonne désignée.|  
|[getSchemaName](../../../connect/jdbc/reference/getschemaname-method-sqlserverresultsetmetadata.md)|Obtient le nom de schéma de la table pour la colonne désignée.|  
|[getTableName](../../../connect/jdbc/reference/gettablename-method-sqlserverresultsetmetadata.md)|Obtient le nom de table de la colonne désignée.|  
|[isAutoIncrement](../../../connect/jdbc/reference/isautoincrement-method-sqlserverresultsetmetadata.md)|Indique si la colonne désignée est numérotée automatiquement, la plaçant ainsi en lecture seule.|  
|[isCaseSensitive](../../../connect/jdbc/reference/iscasesensitive-method-sqlserverresultsetmetadata.md)|Indique si une colonne respecte la casse.|  
|[isCurrency](../../../connect/jdbc/reference/iscurrency-method-sqlserverresultsetmetadata.md)|Indique si la colonne désignée est une valeur de devise.|  
|[isDefinitelyWritable](../../../connect/jdbc/reference/isdefinitelywritable-method-sqlserverresultsetmetadata.md)|Indique si une écriture dans la colonne désignée réussit toujours.|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverresultsetmetadata.md)|Indique l'acceptation des valeurs NULL dans la colonne désignée.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverresultsetmetadata.md)|Indique si la colonne désignée n'accepte jamais d'écriture.|  
|[isSearchable](../../../connect/jdbc/reference/issearchable-method-sqlserverresultsetmetadata.md)|Indique si la colonne désignée peut être utilisée dans une clause SQL WHERE.|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverresultsetmetadata.md)|Indique si les valeurs de la colonne désignée sont des nombres signés.|  
|[isSparseColumnSet](../../../connect/jdbc/reference/issparsecolumnset-method-sqlserverresultsetmetadata.md)|Indique si une colonne dans un jeu de résultats est un jeu de colonnes éparses.|  
|[isWritable](../../../connect/jdbc/reference/iswritable-method-sqlserverresultsetmetadata.md)|Indique si une écriture dans la colonne désignée peut réussir.|  
  
## <a name="inherited-methods"></a>Méthodes héritées  
  
|Classe héritée de :|Méthodes|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
