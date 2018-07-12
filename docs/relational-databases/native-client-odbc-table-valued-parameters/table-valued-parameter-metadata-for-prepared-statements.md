---
title: Métadonnées de paramètre table pour les instructions préparées | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b25c1b075b731d909545abe5f67fa6472477f7f6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427298"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Métadonnées de paramètre table pour les instructions préparées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Une application peut obtenir des métadonnées pour un appel de procédure préparée par le biais SQLNumParams et SQLDescribeParam. Pour les paramètres table, *DataTypePtr* est défini sur SQL_SS_TABLE. Métadonnées supplémentaires sont disponibles via SQLGetDescField pour SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME et SQL_CA_SS_SCHEMA_NAME.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME et SQL_CA_SS_SCHEMA_NAME peuvent être utilisé avec SQLColumns pour obtenir les métadonnées de colonne pour les types de table associés aux paramètres table. Dans ce cas, SQL_SOPT_SS_NAME_SCOPE doit être défini sur SQL_SS_NAME_SCOPE_TABLE_TYPE avant l’appel de SQLColumns. SQL_SOPT_SS_NAME_SCOPE doit ensuite de nouveau être défini sur la valeur par défaut, SQL_SS_NAME_SCOPE_TABLE, lorsque l'application a terminé de récupérer les métadonnées de colonne de paramètre table.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME et SQL_CA_SS_SCHEMA_NAME peuvent également être utilisés avec des paramètres de type CLR défini par l'utilisateur.  
  
 Vous ne pouvez pas obtenir les métadonnées de paramètre table pour les instructions préparées qui ne sont pas des appels de procédure stockée. Si vous essayez, l'application retourne SQL_ERROR avec SQLSTATE 42000 et le message indiquant une erreur de syntaxe ou une violation d'accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
