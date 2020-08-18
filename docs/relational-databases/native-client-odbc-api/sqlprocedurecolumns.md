---
description: SQLProcedureColumns
title: SQLProcedureColumns | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fc569bdb7eab6ce35a68d66829510c23373c25ac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424021"
---
# <a name="sqlprocedurecolumns"></a>SQLProcedureColumns
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SQLProcedureColumns** retourne une ligne signalant les attributs de valeur de retour de toutes les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **SQLProcedureColumns** retourne SQL_SUCCESS qu'il existe ou pas des valeurs pour les paramètres *CatalogName*, *SchemaName*, *ProcName*ou *ColumnName* . **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLProcedureColumns** peut être exécuté sur un curseur côté serveur statique. Une tentative d'exécution de **SQLProcedureColumns** sur un curseur pouvant être mis à jour (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, ce qui indique que le type de curseur a été modifié.  
  
 Le tableau suivant répertorie les colonnes retournées par le jeu de résultats et la façon dont elles ont été étendues pour gérer les types de données **udt** et **xml** via le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client :  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|SS_UDT_CATALOG_NAME|Retourne le nom du catalogue contenant le type défini par l'utilisateur (UDT).|  
|SS_UDT_SCHEMA_NAME|Retourne le nom du schéma contenant l'UDT.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Retourne le nom qualifié de l'assembly du type défini par l'utilisateur (UDT).|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Retourne le nom du catalogue dans lequel un nom de collection de schémas XML est défini. Si le nom du catalogue est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Retourne le nom du schéma dans lequel un nom de collection de schémas XML est défini. Si le nom du schéma est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_NAME|Retourne le nom d'une collection de schémas XML. Si le nom est introuvable, cette variable contient une chaîne vide.|  
  
## <a name="sqlprocedurecolumns-and-table-valued-parameters"></a>SQLProcedureColumns et paramètres table  
 SQLProcedureColumns gère les paramètres table d’une manière similaire aux types CLR définis par l’utilisateur. Dans les lignes retournées pour les paramètres table, les colonnes ont les valeurs suivantes :  
  
|Nom de la colonne|Description/valeur|  
|-----------------|------------------------|  
|DATA_TYPE|SQL_SS_TABLE|  
|TYPE_NAME|Nom du type de table pour le paramètre table.|  
|COLUMN_SIZE|NULL|  
|BUFFER_LENGTH|0|  
|DECIMAL_DIGITS|Nombre de colonnes du paramètre table.|  
|NUM_PREC_RADIX|NULL|  
|NULLABLE|SQL_NULLABLE|  
|Remarques|NULL|  
|COLUMN_DEF|NULL. Les types table ne peuvent pas avoir de valeurs par défaut.|  
|SQL_DATA_TYPE|SQL_SS_TABLE|  
|SQL_DATEIME_SUB|NULL|  
|CHAR_OCTET_LENGTH|NULL|  
|IS_NULLABLE|"YES"|  
|SS_TYPE_CATALOG_NAME|Retourne le nom du catalogue qui contient la table ou le type CLR défini par l'utilisateur.|  
|SS_TYPE_SCHEMA_NAME|Retourne le nom du schéma qui contient la table ou le type CLR défini par l'utilisateur.|  
  
 Les colonnes SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMA_NAME sont disponibles dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures pour retourner, respectivement, le catalogue et le schéma des paramètres table. Ces colonnes sont remplies pour les paramètres table, et également pour les paramètres de type CLR défini par l'utilisateur. (Le schéma et les colonnes de catalogue existants pour les paramètres de type CLR défini par l'utilisateur ne sont pas affectées par ces fonctionnalités supplémentaires. Ils sont également renseignés pour préserver la compatibilité descendante).  
  
 En conformité avec la spécification ODBC, SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMA_NAME apparaissent avant toutes les colonnes spécifiques aux pilotes ajoutées dans les précédentes versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et après toutes les colonnes mandatées par ODBC lui-même.  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLProcedureColumns des fonctionnalités de date et heure améliorées  
 Pour les valeurs retournées pour les types de date/heure, consultez [Catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations générales, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a>Prise en charge par SQLProcedureColumns des grands types CLR définis par l'utilisateur  
 **SQLProcedureColumns** prend en charge les grands types CLR définis par l'utilisateur. Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLProcedureColumns fonction)](https://go.microsoft.com/fwlink/?LinkId=59363)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
