---
title: Métadonnées TVP pour les déclarations préparées
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6928c24b1c06e75c8e20b318321eac4f4bd99985
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297755"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Métadonnées de paramètre table pour les instructions préparées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Une demande peut obtenir des métadonnées pour un appel de procédure préparé par SQLNumParams et SQLDescribeParam. Pour les paramètres de valeur de table, *DataTypePtr* est configuré pour SQL_SS_TABLE. D’autres métadonnées sont disponibles sur SQLGetDescField pour SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME et SQL_CA_SS_SCHEMA_NAME.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME et SQL_CA_SS_SCHEMA_NAME peuvent être utilisés avec SQLColumns pour obtenir des métadonnées de colonne pour les types de table associés aux paramètres de valeur de table. Dans ce cas, SQL_SOPT_SS_NAME_SCOPE doit être réglée pour SQL_SS_NAME_SCOPE_TABLE_TYPE avant l’appel de SQLColumns. SQL_SOPT_SS_NAME_SCOPE doit ensuite de nouveau être défini sur la valeur par défaut, SQL_SS_NAME_SCOPE_TABLE, lorsque l'application a terminé de récupérer les métadonnées de colonne de paramètre table.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME et SQL_CA_SS_SCHEMA_NAME peuvent également être utilisés avec des paramètres de type CLR défini par l'utilisateur.  
  
 Vous ne pouvez pas obtenir les métadonnées de paramètre table pour les instructions préparées qui ne sont pas des appels de procédure stockée. Si vous essayez, l'application retourne SQL_ERROR avec SQLSTATE 42000 et le message indiquant une erreur de syntaxe ou une violation d'accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres évalués par la table &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
