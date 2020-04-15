---
title: SQLColumns - France Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: abce98b64da8de6039f81025201cce25269763a6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302607"
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLColumns** retourne SQL_SUCCESS si des valeurs existent ou non pour les paramètres *CatalogName*, *TableName*, ou *ColumnName.* **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
> [!NOTE]  
>  Pour les types de valeur de grande taille, tous les paramètres « length » sont retournés avec la valeur SQL_SS_LENGTH_UNLIMITED.  
  
 **SQLColumns** peut être exécuté sur un curseur serveur statique. Une tentative d’exécuter **SQLColumns** sur un curseur updatable (dynamique ou keyset) reviendra SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les informations de création de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le paramètre *CatalogName* : *Linked_Server_Name.Catalog_Name*.  
  
 Pour ODBC 2. *x* applications n’utilisant pas de wildcards dans *TableName*, **SQLColumns** renvoie des informations sur les tables dont les noms correspondent *à TableName* et appartiennent à l’utilisateur actuel. Si l’utilisateur actuel ne possède aucune table dont le nom correspond au paramètre *TableName,* **SQLColumns** renvoie des informations sur les tables appartenant à d’autres utilisateurs où le nom de table correspond au paramètre *TableName.* Pour ODBC 2. *x* applications à l’aide de wildcards, **SQLColumns** retourne toutes les tables dont les noms correspondent *à TableName*. Pour ODBC 3. *x* applications **SQLColumns** retourne toutes les tables dont les noms correspondent *à TableName* quel que soit le propriétaire ou si des wildcards sont utilisés.  
  
 Le tableau ci-dessous dresse la liste des colonnes renvoyées par le jeu de résultats :  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|DATA_TYPE|Retourne SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR pour les types de données **varchar(max).**|  
|TYPE_NAME|Retourne "varchar", "varbinary", ou "nvarchar" pour le **varchar(max)**, les types de données **varbinaires(max)** et **nvarchar(max).**|  
|COLUMN_SIZE|Les retours SQL_SS_LENGTH_UNLIMITED pour les types de données **varchar(max)** indiquant que la taille de la colonne est illimitée.|  
|BUFFER_LENGTH|Les retours SQL_SS_LENGTH_UNLIMITED pour les types de données **varchar(max)** indiquant que la taille du tampon est illimitée.|  
|SQL_DATA_TYPE|Retourne SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR pour les types de données **varchar(max).**|  
|CHAR_OCTET_LENGTH|Retourne la longueur maximale d'une colonne de type char ou binary. Retourne 0 pour indiquer que la taille est illimitée.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Retourne le nom du catalogue dans lequel un nom de collection de schémas XML est défini. Si le nom du catalogue est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Retourne le nom du schéma dans lequel un nom de collection de schémas XML est défini. Si le nom du schéma est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_NAME|Retourne le nom d'une collection de schémas XML. Si le nom est introuvable, cette variable contient une chaîne vide.|  
|SS_UDT_CATALOG_NAME|Le nom du catalogue contenant l’UDT (type utilisateur défini).|  
|SS_UDT_SCHEMA_NAME|Le nom du schéma contenant l’UDT.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Nom qualifié de l'assembly du type défini par l'utilisateur (UDT).|  
  
 Pour les UDT, la colonne TYPE_NAME existante est utilisée pour indiquer le nom de l’UDT; donc aucune colonne supplémentaire pour elle ne doit être ajoutée à l’ensemble de résultat de **SQLColumns** ou [SQLProcedureColumns](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md). Le champ DATA_TYPE pour un paramètre ou une colonne de type UDT est SQL_SS_UDT.  
  
 Pour le type UDT des paramètres, vous pouvez utiliser les nouveaux descripteurs spécifiques au pilote définis ci-dessus pour obtenir ou définir les propriétés de métadonnées supplémentaires d'un UDT, si le serveur retourne ou nécessite ces informations.  
  
 Lorsqu’un client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte et appelle SQLColumns, l’utilisation des valeurs NULL ou wild card pour le paramètre d’entrée du catalogue ne renvoie pas les informations d’autres catalogues. Seules les informations sur le catalogue actuel sont retournées. Le client peut d’abord appeler SQLTables pour déterminer dans quel catalogue se trouve la table désirée. Le client peut ensuite utiliser la valeur du catalogue pour le paramètre d’entrée du catalogue dans son appel à SQLColumns pour récupérer des informations sur les colonnes de ce tableau.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns et paramètres table  
 Le résultat retourné par SQLColumns dépend du réglage de SQL_SOPT_SS_NAME_SCOPE. Pour plus d’informations, voir [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Les colonnes suivantes ont été ajoutées pour les paramètres table :  
  
|Nom de la colonne|Type de données|Contents|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Pour une colonne d'un TABLE_TYPE, SQL_TRUE si la colonne est une colonne calculée ; sinon, SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE si la colonne est une colonne d'identité ; sinon, SQL_FALSE.|  
  
 Pour plus d’informations sur les paramètres de valeur de table, voir [Paramètres de valeur de la table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLColumns des fonctionnalités de date et heure améliorées  
 Pour plus d’informations sur les valeurs retournées pour les types de date/heure, voir [Métadonnées catalogu.](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Prise en charge SQLColumns pour les types CLR volumineux définis par l'utilisateur  
 **SQLColumns** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Prise en charge SQLColumns pour les colonnes éparses  
 Deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonnes spécifiques ont été ajoutées au résultat défini pour SQLColumns :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Smallint (Smallint)**|Si la colonne est une colonne éparse, SQL_TRUE ; sinon, SQL_FALSE.|  
|SS_IS_COLUMN_SET|**Smallint (Smallint)**|Si la colonne est la **colonne column_set,** c’est SQL_TRUE; autrement, SQL_FALSE.|  
  
 Conformément aux spécifications de l’ODBC, SS_IS_SPARSE et SS_IS_COLUMN_SET apparaissent devant toutes les colonnes spécifiques au conducteur qui ont été ajoutées aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions plus tôt que, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]et après toutes les colonnes prescrites par ODBC elle-même.  
  
 Le résultat retourné par SQLColumns dépend du réglage de SQL_SOPT_SS_NAME_SCOPE. Pour plus d’informations, voir [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les colonnes clairsemées dans ODBC, voir [Sparse Columns Support &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLColumns](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
