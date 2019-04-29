---
title: SQLColumns | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5815e4f3a0cdd0defb16c613f3d6e9444fdfaac7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63067716"
---
# <a name="sqlcolumns"></a>SQLColumns
  `SQLColumns` Retourne SQL_SUCCESS qu’il existe des valeurs ou non le *CatalogName*, *TableName*, ou *ColumnName* paramètres. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
> [!NOTE]  
>  Pour les types de valeur de grande taille, tous les paramètres « length » sont retournés avec la valeur SQL_SS_LENGTH_UNLIMITED.  
  
 `SQLColumns` peut être exécuté sur un curseur côté serveur statique. Une tentative d'exécution de `SQLColumns` sur un curseur pouvant être mis à jour (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge des informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *CatalogName* paramètre : *Nom_serveur_lié.Nom_Catalogue*.  
  
 Pour ODBC 2. *x* ne pas à l’aide de caractères génériques dans les applications *TableName*, `SQLColumns` retourne des informations sur les tables dont les noms correspondent à *TableName* et sont détenus par l’actuel utilisateur. Si l’utilisateur actuel ne possède aucune table dont le nom correspond à la *TableName* paramètre, `SQLColumns` retourne des informations sur toutes les tables possédées par d’autres utilisateurs dont le nom de la table correspond à la *TableName* paramètre. Pour ODBC 2. *x* applications à l’aide des caractères génériques, `SQLColumns` retourne toutes les tables dont les noms correspondent à *TableName*. Pour ODBC 3. *x* applications `SQLColumns` retourne toutes les tables dont les noms correspondent à *TableName* , quel que soit le propriétaire ou indique si les caractères génériques sont utilisés.  
  
 Le tableau ci-dessous dresse la liste des colonnes renvoyées par le jeu de résultats :  
  
|Nom de colonne|Description|  
|-----------------|-----------------|  
|DATA_TYPE|Retourne SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR pour les **varchar (max)** des types de données.|  
|TYPE_NAME|Retourne « varchar », « varbinary » ou « nvarchar » pour le **varchar (max)**, **varbinary (max)**, et **nvarchar (max)** des types de données.|  
|COLUMN_SIZE|Retourne SQL_SS_LENGTH_UNLIMITED pour **varchar (max)** types de données indiquant que la taille de la colonne est illimitée.|  
|BUFFER_LENGTH|Retourne SQL_SS_LENGTH_UNLIMITED pour **varchar (max)** types de données indiquant que la taille de la mémoire tampon est illimitée.|  
|SQL_DATA_TYPE|Retourne SQL_VARCHAR, SQL_VARBINARY ou SQL_WVARCHAR pour les **varchar (max)** des types de données.|  
|CHAR_OCTET_LENGTH|Retourne la longueur maximale d'une colonne de type char ou binary. Retourne 0 pour indiquer que la taille est illimitée.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Retourne le nom du catalogue dans lequel un nom de collection de schémas XML est défini. Si le nom du catalogue est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Retourne le nom du schéma dans lequel un nom de collection de schémas XML est défini. Si le nom du schéma est introuvable, cette variable contient une chaîne vide.|  
|SS_XML_SCHEMACOLLECTION_NAME|Retourne le nom d'une collection de schémas XML. Si le nom est introuvable, cette variable contient une chaîne vide.|  
|SS_UDT_CATALOG_NAME|Le nom du catalogue contenant l’UDT (type défini par l’utilisateur).|  
|SS_UDT_SCHEMA_NAME|Le nom du schéma contenant l’UDT.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Nom qualifié de l'assembly du type défini par l'utilisateur (UDT).|  
  
 Pour les UDT, la colonne TYPE_NAME existante est utilisée pour indiquer le nom de l’UDT ; Par conséquent aucune colonne supplémentaire correspondante ne doit être ajouté au jeu de résultats de `SQLColumns` ou [SQLProcedureColumns](sqlprocedurecolumns.md). Le champ DATA_TYPE pour un paramètre ou une colonne de type UDT est SQL_SS_UDT.  
  
 Pour le type UDT des paramètres, vous pouvez utiliser les nouveaux descripteurs spécifiques au pilote définis ci-dessus pour obtenir ou définir les propriétés de métadonnées supplémentaires d'un UDT, si le serveur retourne ou nécessite ces informations.  
  
 Quand un client se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et appelle SQLColumns, à l’aide des valeurs NULL ou à caractères génériques pour le paramètre d’entrée de catalogue ne retourne pas d’informations à partir d’autres catalogues. Seules les informations sur le catalogue actuel sont retournées. Le client peut appeler tout d’abord SQLTables pour déterminer dans quel catalogue se trouve la table souhaitée. Le client peut ensuite utiliser cette valeur de catalogue pour le paramètre d’entrée de catalogue dans son appel à SQLColumns pour récupérer des informations sur les colonnes de cette table.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns et paramètres table  
 Le jeu de résultats retourné par SQLColumns dépend de la valeur de SQL_SOPT_SS_NAME_SCOPE. Pour plus d’informations, consultez [SQLSetStmtAttr](sqlsetstmtattr.md). Les colonnes suivantes ont été ajoutées pour les paramètres table :  
  
|Nom de colonne|Type de données|Sommaire|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Pour une colonne d'un TABLE_TYPE, SQL_TRUE si la colonne est une colonne calculée ; sinon, SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE si la colonne est une colonne d'identité ; sinon, SQL_FALSE.|  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLColumns des fonctionnalités de date et heure améliorées  
 Pour plus d’informations sur les valeurs retournées pour les types de date/heure, consultez [métadonnées de catalogue](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations, consultez [améliorations Date / heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>Prise en charge SQLColumns pour les types CLR volumineux définis par l'utilisateur  
 `SQLColumns` prend en charge les grands types CLR définis par l'utilisateur. Pour plus d’informations, consultez [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>Prise en charge SQLColumns pour les colonnes éparses  
 Deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des colonnes spécifiques ont été ajoutés au jeu de résultats pour SQLColumns :  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|`Smallint`|Si la colonne est une colonne éparse, SQL_TRUE ; sinon, SQL_FALSE.|  
|SS_IS_COLUMN_SET|`Smallint`|Si la colonne est la colonne `column_set`, SQL_TRUE ; sinon, SQL_FALSE.|  
  
 Conformément à la spécification ODBC, SS_IS_SPARSE et SS_IS_COLUMN_SET apparaissent avant toutes les colonnes spécifiques au pilote qui ont été ajoutés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]et après toutes les colonnes mandatées par ODBC lui-même.  
  
 Le jeu de résultats retourné par SQLColumns dépend de la valeur de SQL_SOPT_SS_NAME_SCOPE. Pour plus d’informations, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les colonnes éparses dans ODBC, consultez [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLColumns (fonction)](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
