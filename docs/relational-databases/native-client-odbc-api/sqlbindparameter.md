---
title: SQLBindParameter | Microsoft Docs
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
ms.openlocfilehash: cc270cb83833e3fcfc54ef4721a62ccaf3980729
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789433"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  **SQLBindParameter** peut éliminer le fardeau de la conversion des données lorsqu’il est utilisé pour fournir des données pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client, ce qui permet d’obtenir des gains de performances significatifs pour les composants client et serveur des applications. D'autres avantages incluent une perte réduite de précision lors de l'insertion ou de la mise à jour de types de données numériques approximatifs.  
  
> [!NOTE]  
>  Lors de l’insertion de données de type **char** et **WCHAR** dans une colonne image, la taille des données transmises est utilisée, par opposition à la taille des données après conversion dans un format binaire.  
  
 Si le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rencontre une erreur sur un élément de tableau unique d'un tableau de paramètres, le pilote continue d'exécuter l'instruction pour les éléments de tableau restants. Si l'application a lié un tableau d'éléments d'état de paramètre pour l'instruction, les lignes des paramètres qui génèrent des erreurs peuvent être déterminées à partir de ce tableau.  
  
 Lors de l'utilisation du pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, spécifiez SQL_PARAM_INPUT lors de la liaison de paramètres d'entrée. Spécifiez seulement SQL_PARAM_OUTPUT ou SQL_PARAM_INPUT_OUTPUT lors de la liaison de paramètres de procédure stockée définis avec le mot clé OUTPUT.  
  
 [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) n’est pas fiable avec le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client si un élément de tableau d’un tableau de paramètres liés provoque une erreur dans l’exécution de l’instruction. L'attribut d'instruction ODBC SQL_ATTR_PARAMS_PROCESSED_PTR signale le nombre de lignes traitées avant l'erreur. L'application peut alors parcourir son tableau d'état de paramètre pour découvrir le nombre d'instructions exécutées avec succès, si nécessaire.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Liaison de paramètres pour les types de caractères SQL  
 Si le type de données SQL transmis est un type caractère, la valeur de la *colonne column* correspond à la taille en caractères (et non en octets). Si la longueur de la chaîne de données en octets est supérieure à 8000, la valeur de *Column* Size doit être **SQL_SS_LENGTH_UNLIMITED**, ce qui indique qu’il n’existe aucune limite à la taille du type SQL.  
  
 Par exemple, si le type de données SQL est **SQL_WVARCHAR**, la valeur de la *colonne column* ne doit pas être supérieure à 4000. Si la longueur réelle des données est supérieure à 4000, la valeur de la *colonne column* doit être définie sur **SQL_SS_LENGTH_UNLIMITED** afin que **nvarchar (max)** soit utilisé par le pilote.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter et paramètres table  
 Comme les autres types de paramètres, les paramètres table sont liés par SQLBindParameter.  
  
 Une fois qu'un paramètre table a été lié, ses colonnes sont également liées. Pour lier les colonnes, vous appelez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) pour définir SQL_SOPT_SS_PARAM_FOCUS sur l’ordinal du paramètre table. Ensuite, appelez SQLBindParameter pour chaque colonne dans le paramètre table. Pour retourner aux liaisons de paramètre de premier niveau, attribuez à SQL_SOPT_SS_PARAM_FOCUS la valeur 0.  
  
 Pour plus d’informations sur le mappage des paramètres aux champs de descripteur pour les paramètres table, consultez [Binding and transfert de données of Table-valued Parameters and Column Values](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLBindParameter pour les fonctionnalités de date et heure améliorées  
 Les valeurs de paramètre de types date/heure sont converties comme décrit dans [conversions de C en SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md). Notez que les paramètres de type **Time** et **DateTimeOffset** doivent avoir un *ValueType* spécifié comme **SQL_C_DEFAULT** ou **SQL_C_BINARY** si leurs structures correspondantes (**SQL_SS_TIME2_STRUCT** et **SQL_SS_TIMESTAMPOFFSET_STRUCT**) sont utilisées.  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>Prise en charge SQLBindParameter pour les types CLR volumineux définis par l'utilisateur  
 **SQLBindParameter** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de l’implémentation de l’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Fonction SQLBindParameter](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
