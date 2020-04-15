---
title: SQLBindParameter - France Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74122d531eba1f714e16c168838ee1653a8f1293
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302680"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLBindParameter** peut éliminer le fardeau de la conversion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des données lorsqu’il est utilisé pour fournir des données pour le conducteur native ODBC client, résultant en des gains de performance importants pour les composants clients et serveur des applications. D'autres avantages incluent une perte réduite de précision lors de l'insertion ou de la mise à jour de types de données numériques approximatifs.  
  
> [!NOTE]  
>  Lors de l’insertion de données de type **char** et **wchar** dans une colonne d’image, la taille des données transmises est utilisée, par opposition à la taille des données après conversion en format binaire.  
  
 Si le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rencontre une erreur sur un élément de tableau unique d'un tableau de paramètres, le pilote continue d'exécuter l'instruction pour les éléments de tableau restants. Si l'application a lié un tableau d'éléments d'état de paramètre pour l'instruction, les lignes des paramètres qui génèrent des erreurs peuvent être déterminées à partir de ce tableau.  
  
 Lors de l'utilisation du pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, spécifiez SQL_PARAM_INPUT lors de la liaison de paramètres d'entrée. Spécifiez seulement SQL_PARAM_OUTPUT ou SQL_PARAM_INPUT_OUTPUT lors de la liaison de paramètres de procédure stockée définis avec le mot clé OUTPUT.  
  
 [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) n’est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pas fiable avec le conducteur de Native Client ODBC si un élément de tableau d’un tableau lié-paramètre provoque une erreur dans l’exécution de déclaration. L'attribut d'instruction ODBC SQL_ATTR_PARAMS_PROCESSED_PTR signale le nombre de lignes traitées avant l'erreur. L'application peut alors parcourir son tableau d'état de paramètre pour découvrir le nombre d'instructions exécutées avec succès, si nécessaire.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Liaison de paramètres pour les types de caractères SQL  
 Si le type de données SQL transmis est un type de personnage, *ColumnSize* est la taille des caractères (pas les octets). Si la longueur de la chaîne de données dans les octets est supérieure à 8000, *ColumnSize* doit être réglé pour **SQL_SS_LENGTH_UNLIMITED**, ce qui indique qu’il n’y a pas de limite à la taille du type SQL.  
  
 Par exemple, si le type de données SQL est **SQL_WVARCHAR,** *ColumnSize* ne devrait pas être supérieur à 4000. Si la longueur réelle des données est supérieure à 4000, *alors ColumnSize* doit être réglé pour **SQL_SS_LENGTH_UNLIMITED** de sorte que **nvarchar(max)** sera utilisé par le conducteur.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter et paramètres table  
 Comme d’autres types de paramètres, les paramètres de valeur de table sont liés par SQLBindParameter.  
  
 Une fois qu'un paramètre table a été lié, ses colonnes sont également liées. Pour lier les colonnes, vous appelez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) pour régler SQL_SOPT_SS_PARAM_FOCUS à l’ordinaire du paramètre de table. Ensuite, appelez SQLBindParameter pour chaque colonne dans le paramètre de table. Pour retourner aux liaisons de paramètre de premier niveau, attribuez à SQL_SOPT_SS_PARAM_FOCUS la valeur 0.  
  
 Pour plus d’informations sur les paramètres de cartographie des champs descripteurs pour les paramètres évalués par table, voir [le transfert de données et de liaison des paramètres de valeur de la table et les valeurs de colonnes](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Pour plus d’informations sur les paramètres de valeur de table, voir [Paramètres de valeur de la table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLBindParameter pour les fonctionnalités de date et heure améliorées  
 Les valeurs de paramètres des types de date/heure sont converties comme décrit dans [Conversions de C à SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md). Notez que les paramètres de **l’heure** de type et **de l’arrêt de la date** doivent avoir *ValueType* spécifié comme **SQL_C_DEFAULT** ou **SQL_C_BINARY** si leurs structures correspondantes **(SQL_SS_TIME2_STRUCT** et **SQL_SS_TIMESTAMPOFFSET_STRUCT**) sont utilisées.  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>Prise en charge SQLBindParameter pour les types CLR volumineux définis par l'utilisateur  
 **SQLBindParameter** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de la mise en œuvre de l’ODBC API](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Fonction SQLBindParameter](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
