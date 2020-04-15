---
title: SQLTables - France Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3f3fa2b053c41facba7d608b2352772abd3ff103
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291737"
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLTables peut être exécuté sur un curseur serveur statique. Une tentative d’exécuter SQLTables sur un curseur updatable (dynamique ou keyset) reviendra SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
 SQLTables rapporte les tableaux de toutes les bases de données lorsque le paramètre *CatalogName* est SQL_ALL_CATALOGS et que tous les autres paramètres contiennent des valeurs par défaut (pointeurs NULL).  
  
 Pour signaler les catalogues, les schémas et les types de table disponibles, SQLTables utilise particulièrement les cordes vides (pointeurs d’ente de longueur zéro). Les chaînes vides ne sont pas des valeurs par défaut (pointeurs NULL).  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les informations de création de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le paramètre *CatalogName* : *Linked_Server_Name.Catalog_Name*.  
  
 SQLTables renvoie des informations sur toutes les tables dont les noms correspondent *à TableName* et appartiennent à l’utilisateur actuel.  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables et paramètres table  
 Lorsque l’attribut de l’énoncé SQL_SOPT_SS_NAME_SCOPE a la valeur SQL_SS_NAME_SCOPE_TABLE_TYPE, plutôt que sa valeur par défaut de SQL_SS_NAME_SCOPE_TABLE, SQLTables renvoie des informations sur les types de tables. La valeur TABLE_TYPE retournée pour un type de table dans la colonne 4 du résultat établi par SQLTables est TABLE TYPE. Pour plus d'informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Les tables, les vues et les synonymes partagent un espace de noms commun, distinct de l'espace de noms utilisé par les types de table. Bien qu'il ne soit pas possible d'avoir une table et une vue ayant le même nom, vous pouvez avoir une table et un type de table avec le même nom dans le même catalogue et le même schéma.  
  
 Pour plus d’informations sur les paramètres de valeur de table, voir [Paramètres de valeur de la table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Exemple  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLTables](https://go.microsoft.com/fwlink/?LinkId=59374)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
