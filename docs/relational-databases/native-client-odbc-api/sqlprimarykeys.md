---
title: SQLPrimaryKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c2ee83335e00c3129d73c26db37d40af2375c410
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73786047"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Une table peut avoir une ou plusieurs colonnes pouvant servir d’identificateurs de ligne uniques, et les tables créées sans contrainte de clé primaire renvoient un jeu de résultats vide à SQLPrimaryKeys. La fonction ODBC [SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md) signale les candidats aux identificateurs de ligne pour les tables sans clés primaires.  
  
 SQLPrimaryKeys retourne SQL_SUCCESS si des valeurs existent pour les paramètres *nomcatalogue*, *SchemaName*ou *TableName* . SQLFetch retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 SQLPrimaryKeys peut être exécuté sur un curseur côté serveur statique. Une tentative d’exécution de SQLPrimaryKeys sur un curseur pouvant être mis à jour (dynamique ou de jeu de clés) retourne SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les informations de création de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le paramètre *CatalogName* : *Linked_Server_Name.Catalog_Name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys et paramètres table  
 Si l’attribut d’instruction SQL_SOPT_SS_NAME_SCOPE a la valeur SQL_SS_NAME_SCOPE_TABLE_TYPE, plutôt que sa valeur par défaut de SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys renvoie des informations sur les colonnes de clé primaire des types de table. Pour plus d'informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLPrimaryKeys fonction)](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
