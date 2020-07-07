---
title: Métadonnées de paramètres table supplémentaires | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), catalog functions to retrieve metadata
- table-valued parameters (ODBC), metadata
ms.assetid: 6c193188-5185-4373-9a0d-76cfc150c828
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1aed8844cffc6ccfb6608e4077f792dcf8651e6
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004607"
---
# <a name="additional-table-valued-parameter-metadata"></a>Métadonnées de paramètres table supplémentaires
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Pour récupérer les métadonnées d’un paramètre table, une application appelle SQLProcedureColumns. Pour un paramètre table, SQLProcedureColumns retourne une ligne unique. Deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonnes spécifiques supplémentaires, SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMA_NAME, ont été ajoutées pour fournir des informations de schéma et de catalogue pour les types de tables associés aux paramètres table. En conformité avec la spécification ODBC, SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMA_NAME apparaissent avant toutes les colonnes spécifiques aux pilotes ajoutées dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et après toutes les colonnes mandatées par ODBC lui-même.  
  
 Le tableau suivant répertorie les colonnes significatives pour les paramètres table.  
  
|Nom de la colonne|Type de données|Valeur/commentaires|  
|-----------------|---------------|---------------------|  
|DATA_TYPE|Smallint non NULL|SQL_SS_TABLE|  
|TYPE_NAME|WVarchar (128) non NULL|Nom du type du paramètre table.|  
|COLUMN_SIZE|Integer|NULL|  
|BUFFER_LENGTH|Integer|0|  
|DECIMAL_DIGITS|Smallint|NULL|  
|NUM_PREC_RADIX|Smallint|NULL|  
|NULLABLE|Smallint non NULL|SQL_NULLABLE|  
|REMARQUES|Varchar|NULL|  
|COLUMN_DEF|WVarchar(4000)|NULL|  
|SQL_DATA_TYPE|Smallint non NULL|SQL_SS_TABLE|  
|SQL_DATETIME_SUB|Smallint|NULL|  
|CHAR_OCTET_LENGTH|Integer|NULL|  
|ORDINAL_POSITION|Entier non NULL|Position ordinale du paramètre.|  
|IS_NULLABLE|Varchar|"YES"|  
|SS_TYPE_CATALOG_NAME|WVarchar (128) non NULL|Catalogue contenant la définition de type pour le type de table du paramètre table.|  
|SS_TYPE_SCHEMA_NAME|WVarchar (128) non NULL|Schéma contenant la définition de type pour le type de table du paramètre table.|  
  
 Les colonnes WVarchar sont définies comme Varchar dans la spécification ODBC, mais sont de fait retournées comme WVarchar dans les pilotes ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les plus récents. Cette modification a été apportée lorsque la prise en charge Unicode a été ajoutée à la spécification ODBC 3.5, sans être appelée explicitement.  
  
 Pour obtenir des métadonnées supplémentaires pour les paramètres table, une application utilise les fonctions de catalogue SQLColumns et SQLPrimaryKeys. Avant que ces fonctions ne soient appelées pour les paramètres table, l'application doit définir l'attribut d'instruction SQL_SOPT_SS_NAME_SCOPE avec la valeur SQL_SS_NAME_SCOPE_TABLE_TYPE. Cette valeur indique que l'application requiert les métadonnées pour un type table plutôt qu'une table réelle. L’application passe ensuite la TYPE_NAME du paramètre table comme paramètre *TableName* . SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMA_NAME sont respectivement utilisés avec les paramètres *nomcatalogue* et *SchemaName* pour identifier le catalogue et le schéma du paramètre table. Quand une application a fini d'extraire les métadonnées des paramètres table, elle doit redéfinir SQL_SOPT_SS_NAME_SCOPE avec sa valeur par défaut SQL_SS_NAME_SCOPE_TABLE.  
  
 Lorsque SQL_SOPT_SS_NAME_SCOPE est défini avec la valeur SQL_SS_NAME_SCOPE_TABLE, les requêtes adressées aux serveurs liés échouent. Les appels à SQLColumns ou SQLPrimaryKeys avec un catalogue qui contient un composant serveur échouent.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
