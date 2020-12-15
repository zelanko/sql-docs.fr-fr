---
description: SQLColumns
title: SQLColumns | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 73bdc833b31251e3cf0747aca19371ad2b0cb839
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473770"
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SQLColumns** retourne SQL_SUCCESS que des valeurs existent ou non pour les paramètres *nomcatalogue*, *TableName* ou *ColumnName* . **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
> [!NOTE]  
>  Pour les types de valeur de grande taille, tous les paramètres « length » sont retournés avec la valeur SQL_SS_LENGTH_UNLIMITED.  
  
 **SQLColumns** peut être exécuté sur un curseur côté serveur statique. Une tentative d’exécution de **SQLColumns** sur un curseur pouvant être mis à jour (dynamique ou de jeu de clés) retourne SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les informations de création de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le paramètre *CatalogName* : *Linked_Server_Name.Catalog_Name*.  
  
 Pour ODBC 2. *x* applications qui n’utilisent pas de caractères génériques dans *TableName*, **SQLColumns** retourne des informations sur toutes les tables dont les noms correspondent à *TableName* et qui sont détenues par l’utilisateur actuel. Si l’utilisateur actuel ne possède pas de table dont le nom correspond au paramètre *TableName* , **SQLColumns** retourne des informations sur toutes les tables détenues par d’autres utilisateurs où le nom de la table correspond au paramètre *TableName* . Pour ODBC 2. *x* applications utilisant des caractères génériques, **SQLColumns** retourne toutes les tables dont les noms correspondent à *TableName*. Pour ODBC 3. *x* applications **SQLColumns** retourne toutes les tables dont les noms correspondent à *TableName* , quel que soit le propriétaire ou si des caractères génériques sont utilisés.  
  
 Le tableau ci-dessous dresse la liste des colonnes renvoyées par le jeu de résultats :  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|DATA_TYPE|Retourne SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR pour les types de données **varchar (max)** .|  
|TYPE_NAME|Retourne "varchar", "varbinary" ou "nvarchar" pour les types de données **varchar (max)**, **varbinary (max)** et **nvarchar (max)** .|  
|COLUMN_SIZE|Retourne SQL_SS_LENGTH_UNLIMITED pour les types de données **varchar (max)** indiquant que la taille de la colonne est illimitée.|  
|BUFFER_LENGTH|Retourne SQL_SS_LENGTH_UNLIMITED pour les types de données **varchar (max)** indiquant que la taille de la mémoire tampon est illimitée.|  
|SQL_DATA_TYPE|Retourne SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR pour les types de données **varchar (max)** .|  
|CHAR_OCTET_LENGTH|Retourne la longueur maximale d'une colonne de type char ou binary. Retourne 0 pour indiquer que la taille est illimitée.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Retourne le nom du catalogue dans lequel un nom de collection de schémas XML est défini. Si le nom du catalogue est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Retourne le nom du schéma dans lequel un nom de collection de schémas XML est défini. Si le nom du schéma est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_NAME|Retourne le nom d'une collection de schémas XML. Si le nom est introuvable, cette variable contient une chaîne vide.|  
|SS_UDT_CATALOG_NAME|Nom du catalogue contenant le type défini par l’utilisateur (UDT).|  
|SS_UDT_SCHEMA_NAME|Nom du schéma contenant le type défini par l’utilisateur.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Nom qualifié de l'assembly du type défini par l'utilisateur (UDT).|  
  
 Pour les UDT, la colonne TYPE_NAME existante est utilisée pour indiquer le nom du type défini par l’utilisateur ; par conséquent, aucune colonne supplémentaire ne doit être ajoutée au jeu de résultats de **SQLColumns** ou de [SQLProcedureColumns](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md). Le champ DATA_TYPE pour un paramètre ou une colonne de type UDT est SQL_SS_UDT.  
  
 Pour le type UDT des paramètres, vous pouvez utiliser les nouveaux descripteurs spécifiques au pilote définis ci-dessus pour obtenir ou définir les propriétés de métadonnées supplémentaires d'un UDT, si le serveur retourne ou nécessite ces informations.  
  
 Lorsqu’un client se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLColumns, l’utilisation de valeurs null ou de caractères génériques pour le paramètre d’entrée de catalogue ne retourne pas d’informations à partir d’autres catalogues. Seules les informations sur le catalogue actuel sont retournées. Le client peut tout d’abord appeler SQLTables pour déterminer dans quel catalogue se trouve la table souhaitée. Le client peut ensuite utiliser cette valeur de catalogue pour le paramètre d’entrée de catalogue dans son appel à SQLColumns pour extraire des informations sur les colonnes de cette table.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns et paramètres table  
 Le jeu de résultats retourné par SQLColumns dépend du paramètre de SQL_SOPT_SS_NAME_SCOPE. Pour plus d’informations, consultez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Les colonnes suivantes ont été ajoutées pour les paramètres table :  
  
|Nom de la colonne|Type de données|Contenu|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Pour une colonne d'un TABLE_TYPE, SQL_TRUE si la colonne est une colonne calculée ; sinon, SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE si la colonne est une colonne d'identité ; sinon, SQL_FALSE.|  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLColumns des fonctionnalités de date et heure améliorées  
 Pour plus d’informations sur les valeurs retournées pour les types date/heure, consultez [métadonnées de catalogue](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Prise en charge SQLColumns pour les types CLR volumineux définis par l'utilisateur  
 **SQLColumns** prend en charge les grands types CLR définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types de User-Defined CLR volumineux &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Prise en charge SQLColumns pour les colonnes éparses  
 Deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonnes spécifiques ont été ajoutées au jeu de résultats pour SQLColumns :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Smallint**|Si la colonne est une colonne éparse, SQL_TRUE ; sinon, SQL_FALSE.|  
|SS_IS_COLUMN_SET|**Smallint**|Si la colonne est la colonne **column_set** , il s’agit de SQL_TRUE ; Sinon, SQL_FALSE.|  
  
 En conformité avec la spécification ODBC, SS_IS_SPARSE et SS_IS_COLUMN_SET apparaissent avant toutes les colonnes spécifiques au pilote qui ont été ajoutées aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , et après toutes les colonnes mandatées par ODBC lui-même.  
  
 Le jeu de résultats retourné par SQLColumns dépend du paramètre de SQL_SOPT_SS_NAME_SCOPE. Pour plus d’informations, consultez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les colonnes éparses dans ODBC, consultez [prise en charge des colonnes éparses &#40;odbc&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLColumns](../../odbc/reference/syntax/sqlcolumns-function.md)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
