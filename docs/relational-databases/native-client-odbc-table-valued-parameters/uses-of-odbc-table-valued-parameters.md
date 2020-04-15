---
title: Utilisations de paramètres de valeur de la table ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), scenarios
- ODBC, table-valued parameters
ms.assetid: f1b73932-4570-4a8a-baa0-0f229d9c32ee
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e88092c6566d9e5838f8a2cb59cd7c23564af9b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297733"
---
# <a name="uses-of-odbc-table-valued-parameters"></a>Scénarios d'utilisation des paramètres table ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique présente les principaux scénarios utilisateur dans lesquels des paramètres table sont utilisés avec ODBC :  
  
-   Paramètre table avec mémoires tampons multilignes entièrement liées (envoyer des données en tant que paramètre table avec toutes les valeurs en mémoire)  
  
-   Paramètre table avec diffusion de lignes en continu (envoyer des données en tant que paramètre table à l'aide de données en cours d'exécution)  
  
-   Récupération des métadonnées de paramètre table du catalogue système  
  
-   Récupération des métadonnées de paramètre table pour une instruction préparée  
  
## <a name="table-valued-parameter-with-fully-bound-multirow-buffers-send-data-as-a-tvp-with-all-values-in-memory"></a>Paramètre table avec mémoires tampons multilignes entièrement liées (envoyer des données en tant que paramètre table avec toutes les valeurs en mémoire)  
 Lorsqu'elles sont utilisées avec des mémoires tampons multilignes entièrement liées, toutes les valeurs de paramètres sont disponibles en mémoire. Ce comportement est classique d'une transaction OLTP par exemple, dans laquelle les paramètres table peuvent être insérés dans une procédure stockée unique. Sans paramètres table, il serait nécessaire de générer dynamiquement un lot à instructions multiples complexe ou d'effectuer plusieurs appels au serveur.  
  
 Le paramètre de valeur de table lui-même est lié par l’utilisation [de SQLBindParameter](https://go.microsoft.com/fwlink/?LinkId=59328) avec les autres paramètres. Une fois que tous les paramètres ont été liés, l’application définit l’attribut de mise au point de paramètres, SQL_SOPT_SS_PARAM_FOCUS, sur chaque paramètre de table et appelle SQLBindParameter pour les colonnes du paramètre de table.  
  
 Le type de serveur d'un paramètre table est un nouveau type spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SQL_SS_TABLE. Le type C de liaison pour SQL_SS_TABLE doit toujours être SQL_C_DEFAULT. Aucune donnée n'est transférée pour le paramètre lié au paramètre table ; il est utilisé pour passer les métadonnées de table et contrôler comment passer des données dans les colonnes qui constituent le paramètre table.  
  
 La longueur du paramètre table est définie sur le nombre de lignes qui sont envoyées au serveur. Le *paramètre ColumnSize* de SQLBindParameter pour un paramètre évalué à la table spécifie le nombre maximal de lignes qui peuvent être envoyées; c’est la taille du tableau des tampons de colonne. *ParavaluePtr* est le paramètre tampon, pour un paramètre de valeur de table dans SQLBindParameter. *ParamètreValuePtr* et son *BufferLength* associé sont utilisés pour passer le nom type du paramètre de valeur de table au besoin. Le nom de type n'est pas requis pour les appels de procédure stockée, mais il est requis pour les instructions SQL.  
  
 Lorsqu’un nom de type paramètre de valeur de table est spécifié lors d’un appel à SQLBindParameter, il doit toujours être spécifié comme une valeur Unicode, même dans les applications qui sont construites sous forme d’applications ANSI. Lorsque vous spécifiez un nom de type paramètre de valeur de table en utilisant SQLSetDescField, vous pouvez utiliser un littéral conforme à la façon dont l’application est construite. Le Gestionnaire de pilotes ODBC effectuera toute conversion Unicode requise.  
  
 Les métadonnées pour les paramètres de valeur de table et les colonnes de paramètres de valeur de table peuvent être manipulées individuellement et explicitement en utilisant SQLGetDescRec, SQLSetDescRec, SQLGetDescField et SQLSetDescField. Cependant, la surcharge SQLBindParameter est généralement plus pratique et ne nécessite pas d’accès explicite descripteur dans la plupart des cas. Cette approche est conforme à la définition de SQLBindParameter pour d’autres types de données, sauf que pour un paramètre de valeur de table, les champs descripteur touchés sont légèrement différents.  
  
 Une application utilise parfois un paramètre table avec Dynamic SQL et le nom de type du paramètre table doit être fourni. Si c’est le cas et que le paramètre évalué par la table n’est pas défini dans le schéma par défaut actuel pour la connexion, SQL_CA_SS_TYPE_CATALOG_NAME et SQL_CA_SS_TYPE_SCHEMA_NAME doivent être définis à l’aide de SQLSetDescField. Dans la mesure où les définitions de type de table et les paramètres table doivent se trouver dans la même base de données, SQL_CA_SS_TYPE_CATALOG_NAME ne doit pas être défini si l'application utilise des paramètres table. Dans le cas contraire, SQLSetDescField signalera une erreur.  
  
 Le code d’échantillon pour `demo_fixed_TVP_binding` ce scénario est dans la procédure dans [l’utilisation des paramètres de valeur de table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="table-valued-parameter-with-row-streaming-send-data-as-a-tvp-using-data-at-execution"></a>Paramètre table avec diffusion de lignes en continu (envoyer des données en tant que paramètre table à l'aide de données en cours d'exécution)  
 Dans ce scénario, l'application fournit des lignes au pilote quand il les lui demande et ces lignes sont transmises en continu au serveur. Ainsi, il n'est pas nécessaire que toutes les lignes soient mises en mémoire tampon. Ceci est représentatif des scénarios d'insertion/mise à jour en bloc. Les performances des paramètres table se situent entre les tableaux de paramètres et la copie en bloc. Autrement dit, les paramètres table sont pratiquement aussi faciles à programmer que les tableaux de paramètres, mais offrent une souplesse supérieure au niveau du serveur.  
  
 Le paramètre table et ses colonnes sont liés comme discuté dans la section précédente, Paramètre table avec mémoires tampons multilignes entièrement liées, mais l'indicateur de longueur du paramètre table lui-même est défini sur SQL_DATA_AT_EXEC. Le conducteur répond à SQLExecute ou SQLExecuteDirect de la manière habituelle pour les paramètres de données à l’exécution, c’est-à-dire en retournant SQL_NEED_DATA. Lorsque le conducteur est prêt à accepter des données pour un paramètre de valeur de table, SQLParamData retourne la valeur de *ParameterValuePtr* dans SQLBindParameter.  
  
 Une application utilise SQLPutData pour un paramètre de valeur de table pour indiquer la disponibilité de données pour les colonnes constituantes de paramètres de valeur de table. Lorsque SQLPutData est appelé pour un paramètre de valeur de table, *DataPtr* doit toujours être nul et *StrLen_or_Ind* doit être soit 0 ou un nombre inférieur ou égal à la taille du tableau spécifié pour les tampons de paramètres de valeur de table (le paramètre *ColumnSize* de SQLBindParameter). 0 signifie qu'il n'y a plus de lignes pour le paramètre table et que le pilote passera au traitement du paramètre de procédure réel suivant. Lorsque *StrLen_or_Ind* n’est pas 0, le conducteur traitera les colonnes constituantes de paramètres de valeur de table de la même manière que les paramètres liés aux paramètres non évalués par table : chaque colonne de paramètres évaluée en table peut spécifier sa longueur de données réelle, SQL_NULL_DATA, ou il peut spécifier des données à l’exécution via son tampon de longueur/indicateur. Les valeurs de colonne de paramètres évaluées par table peuvent être transmises par des appels répétés à SQLPutData comme d’habitude lorsqu’un personnage ou une valeur binaire doit être transmis en morceaux.  
  
 Une fois toutes les colonnes de paramètre table traitées, le pilote revient au paramètre table pour traiter d'autres lignes de données de paramètre table. Par conséquent, pour les paramètres table de données en cours d'exécution, le pilote ne suit pas l'analyse séquentielle habituelle des paramètres liés. Un paramètre lié de valeur de table sera sondé jusqu’à ce que SQLPutData soit appelé avec *StrLen_Or_IndPtr* égale à 0, date à laquelle le conducteur saute des colonnes de paramètres de valeur de table et passe au paramètre de procédure stocké réel suivant.  Lorsque SQLPutData passe une valeur d’indicateur supérieure ou égale à 1, le conducteur traite des colonnes de paramètres et des rangées de table séquentiellement jusqu’à ce qu’il ait des valeurs pour toutes les lignes et colonnes liées. Le pilote revient ensuite au paramètre table. Entre la réception du jeton pour le paramètre évalué à la table de SQLParamData et l’appel SQLPutData (hstmt, NULL, n) pour un paramètre évalué à la table, l’application doit définir des données de colonne constituante de définition de table et le contenu tampon d’indicateur pour la prochaine rangée ou lignes à passer au serveur.  
  
 Le code d’échantillon pour `demo_variable_TVP_binding` ce scénario est dans la routine dans [l’utilisation des paramètres de valeur de table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-from-the-system-catalog"></a>Récupération des métadonnées de paramètre table du catalogue système  
 Lorsqu’une demande appelle SQLProcedureColumns pour une procédure dont les paramètres de valeur de table sont évalués, DATA_TYPE est retournée comme SQL_SS_TABLE et TYPE_NAME est le nom du type de table pour le paramètre évalué à la table. Deux colonnes supplémentaires sont ajoutées à l’ensemble de résultat retourné par SQLProcedureColumns : SS_TYPE_CATALOG_NAME renvoie le nom du catalogue où le type de tableau du paramètre de valeur de la table est défini, et SS_TYPE_SCHEMA_NAME renvoie le nom du schéma où le type de table du paramètre de valeur de table est défini. Conformément à la spécification ODBC, SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMA_NAME apparaissent avant toutes les colonnes spécifiques au pilote qui ont été ajoutées dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et après toutes les colonnes mandatées par ODBC lui-même.  
  
 Les nouvelles colonnes seront remplies à la fois pour les paramètres table, mais aussi pour les paramètres du type CLR défini par l'utilisateur. Les colonnes de schéma et de catalogue existantes des paramètres définis par l'utilisateur continuent d'être remplies, mais le fait de disposer de colonnes de schéma et de catalogue communes pour les types de données qui en ont besoin simplifie le développement d'applications dans le futur. (Notez que les collections de schémas XML sont quelque peu différentes et ne sont pas incluses dans cette modification.)  
  
 Une application utilise SQLTables pour déterminer les noms des types de table de la même façon qu’elle le fait pour les tables persistantes, les tables système et les vues. Un nouveau type de table, TABLE TYPE, est introduit pour permettre à une application d'identifier les types de tables associés aux paramètres table. Les types de tables et les tables standard utilisent des espaces de noms différents. Cela signifie que vous pouvez utiliser le même nom pour un type de table et pour une table réelle. À cet effet, un nouvel attribut d'instruction, SQL_SOPT_SS_NAME_SCOPE, a été introduit. Cet attribut précise si SQLTables et d’autres fonctions de catalogue qui prennent un nom de table comme paramètre doivent interpréter le nom de table comme le nom d’une table réelle ou le nom d’un type de table.  
  
 Une application utilise SQLColumns pour déterminer les colonnes pour un type de table de la même manière qu’elle le fait pour les tables persistantes, mais doit d’abord définir SQL_SOPT_SS_NAME_SCOPE pour indiquer qu’il travaille avec des types de table plutôt que des tables réelles. SQLPrimaryKeys peut également être utilisé avec des types de table, encore une fois en utilisant SQL_SOPT_SS_NAME_SCOPE.  
  
 Le code d’échantillon pour `demo_metadata_from_catalog_APIs` ce scénario est dans la routine dans [l’utilisation des paramètres de valeur de table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-for-a-prepared-statement"></a>Récupération des métadonnées de paramètre table pour une instruction préparée  
 Dans ce scénario, une application utilise SQLNumParameters et SQLDescribeParam pour récupérer des métadonnées pour des paramètres de valeur de table.  
  
 Le champ IPD SQL_CA_SS_TYPE_NAME est utilisé pour récupérer le nom du type du paramètre table. Les champs IPD SQL_CA_SS_TYPE_SCHEMA_NAME et SQL_CA_SS_TYPE_CATALOG_NAME sont utilisés pour récupérer respectivement son catalogue et son schéma.  
  
 Les définitions de types de tables et les paramètres table doivent se trouver dans la même base de données. SQLSetDescField signalera une erreur si une application établit SQL_CA_SS_TYPE_CATALOG_NAME lors de l’utilisation de paramètres de valeur de table.  
  
 SQL_CA_SS_TYPE_CATALOG_NAME et SQL_CA_SS_TYPE_SCHEMA_NAME peuvent également être utilisés pour récupérer le catalogue et le schéma associés aux paramètres du type CLR défini par l'utilisateur. SQL_CA_SS_TYPE_CATALOG_NAME et SQL_CA_SS_TYPE_SCHEMA_NAME sont des alternatives aux attributs existants de schéma de catalogue spécifiques au type pour les types CLR définis par l'utilisateur.  
  
 Une application utilise SQLColumns pour récupérer les métadonnées de colonne pour un paramètre de table dans ce scénario, aussi, parce que SQLDescribeParam ne retourne pas les métadonnées pour les colonnes d’une colonne de paramètres de table.  
  
 Le code d’échantillon pour `demo_metadata_from_prepared_statement` ce cas d’utilisation est dans la routine dans [l’utilisation des paramètres de valeur de table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres évalués par la table &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
