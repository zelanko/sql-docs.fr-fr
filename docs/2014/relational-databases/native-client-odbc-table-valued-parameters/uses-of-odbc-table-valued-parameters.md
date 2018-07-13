---
title: Utilisation des paramètres de Table-Valued ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), scenarios
- ODBC, table-valued parameters
ms.assetid: f1b73932-4570-4a8a-baa0-0f229d9c32ee
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1de1e1222d53aad02c4aee4eab2db0aaf5f8bd0e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407729"
---
# <a name="uses-of-odbc-table-valued-parameters"></a>Scénarios d'utilisation des paramètres table ODBC
  Cette rubrique présente les principaux scénarios utilisateur dans lesquels des paramètres table sont utilisés avec ODBC :  
  
-   Paramètre table avec mémoires tampons multilignes entièrement liées (envoyer des données en tant que paramètre table avec toutes les valeurs en mémoire)  
  
-   Paramètre table avec diffusion de lignes en continu (envoyer des données en tant que paramètre table à l'aide de données en cours d'exécution)  
  
-   Récupération des métadonnées de paramètre table du catalogue système  
  
-   Récupération des métadonnées de paramètre table pour une instruction préparée  
  
## <a name="table-valued-parameter-with-fully-bound-multirow-buffers-send-data-as-a-tvp-with-all-values-in-memory"></a>Paramètre table avec mémoires tampons multilignes entièrement liées (envoyer des données en tant que paramètre table avec toutes les valeurs en mémoire)  
 Lorsqu'elles sont utilisées avec des mémoires tampons multilignes entièrement liées, toutes les valeurs de paramètres sont disponibles en mémoire. Ce comportement est classique d'une transaction OLTP par exemple, dans laquelle les paramètres table peuvent être insérés dans une procédure stockée unique. Sans paramètres table, il serait nécessaire de générer dynamiquement un lot à instructions multiples complexe ou d'effectuer plusieurs appels au serveur.  
  
 Le paramètre table lui-même est lié à l’aide de [SQLBindParameter](http://go.microsoft.com/fwlink/?LinkId=59328) avec les autres paramètres. Une fois que tous les paramètres ont été liés, l’application définit l’attribut de focus de paramètre, SQL_SOPT_SS_PARAM_FOCUS, sur chaque paramètre table et appelle SQLBindParameter pour les colonnes du paramètre table incluse.  
  
 Le type de serveur d'un paramètre table est un nouveau type spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SQL_SS_TABLE. Le type C de liaison pour SQL_SS_TABLE doit toujours être SQL_C_DEFAULT. Aucune donnée n'est transférée pour le paramètre lié au paramètre table ; il est utilisé pour passer les métadonnées de table et contrôler comment passer des données dans les colonnes qui constituent le paramètre table.  
  
 La longueur du paramètre table est définie sur le nombre de lignes qui sont envoyées au serveur. Le *ColumnSize* paramètre de SQLBindParameter pour un paramètre table spécifie le nombre maximal de lignes qui peuvent être envoyées ; c’est la taille du tableau de mémoires tampons de la colonne. *ParameterValuePtr* est la mémoire tampon de paramètre pour un paramètre table dans SQLBindParameter. *ParameterValuePtr* et elle est associée *BufferLength* sont utilisés pour passer le nom de type du paramètre table incluse si nécessaire. Le nom de type n'est pas requis pour les appels de procédure stockée, mais il est requis pour les instructions SQL.  
  
 Lorsqu’un nom de type de paramètre table est spécifié sur un appel à SQLBindParameter, il doit toujours être spécifié comme une valeur Unicode, même dans les applications qui sont générées comme applications ANSI. Lorsque vous spécifiez un nom de type de paramètre table à l’aide de SQLSetDescField, vous pouvez utiliser un littéral conforme à la façon dont l’application est générée. Le Gestionnaire de pilotes ODBC effectuera toute conversion Unicode requise.  
  
 Métadonnées de paramètres table et des colonnes de paramètre table peuvent être manipulées individuellement et explicitement à l’aide de SQLGetDescRec, SQLSetDescRec, SQLGetDescField et SQLSetDescField. Toutefois, la surcharge de SQLBindParameter est généralement plus pratique et ne nécessite pas d’accès à des descripteurs dans la plupart des cas. Cette approche est cohérente avec la définition de SQLBindParameter pour les autres types de données, à ceci près que pour un paramètre table, les champs de descripteur affectés sont légèrement différentes.  
  
 Une application utilise parfois un paramètre table avec Dynamic SQL et le nom de type du paramètre table doit être fourni. Si c’est le cas et le paramètre table n’est pas défini dans le schéma par défaut actuel pour la connexion, SQL_CA_SS_TYPE_CATALOG_NAME et SQL_CA_SS_TYPE_SCHEMA_NAME doivent être définie à l’aide de SQLSetDescField. Dans la mesure où les définitions de type de table et les paramètres table doivent se trouver dans la même base de données, SQL_CA_SS_TYPE_CATALOG_NAME ne doit pas être défini si l'application utilise des paramètres table. Sinon, SQLSetDescField signalera une erreur.  
  
 Exemple de code pour ce scénario se trouve dans la procédure `demo_fixed_TVP_binding` dans [utiliser les paramètres &#40;ODBC&#41;](../native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="table-valued-parameter-with-row-streaming-send-data-as-a-tvp-using-data-at-execution"></a>Paramètre table avec diffusion de lignes en continu (envoyer des données en tant que paramètre table à l'aide de données en cours d'exécution)  
 Dans ce scénario, l'application fournit des lignes au pilote quand il les lui demande et ces lignes sont transmises en continu au serveur. Ainsi, il n'est pas nécessaire que toutes les lignes soient mises en mémoire tampon. Ceci est représentatif des scénarios d'insertion/mise à jour en bloc. Les performances des paramètres table se situent entre les tableaux de paramètres et la copie en bloc. Autrement dit, les paramètres table sont pratiquement aussi faciles à programmer que les tableaux de paramètres, mais offrent une souplesse supérieure au niveau du serveur.  
  
 Le paramètre table et ses colonnes sont liés comme discuté dans la section précédente, Paramètre table avec mémoires tampons multilignes entièrement liées, mais l'indicateur de longueur du paramètre table lui-même est défini sur SQL_DATA_AT_EXEC. Le pilote répond à SQLExecute ou SQLExecuteDirect de la manière habituelle pour les paramètres de data-at-execution, autrement dit, en retournant SQL_NEED_DATA. Lorsque le pilote est prêt à accepter des données pour un paramètre table, SQLParamData retourne la valeur de *ParameterValuePtr* dans SQLBindParameter.  
  
 Une application utilise SQLPutData pour un paramètre table pour indiquer la disponibilité des données pour les colonnes constituantes des paramètres table. Lorsque SQLPutData est appelée pour un paramètre table, *DataPtr* doit toujours être null et *StrLen_or_Ind* doit être 0 ou un nombre inférieur ou égal à la taille du tableau spécifiée pour table-valued mémoires tampons de paramètres (le *ColumnSize* paramètre de SQLBindParameter). 0 signifie qu'il n'y a plus de lignes pour le paramètre table et que le pilote passera au traitement du paramètre de procédure réel suivant. Lorsque *StrLen_or_Ind* est pas égal à 0, le pilote traite les colonnes qui constituent de paramètre table dans la même façon comme paramètre non – table des paramètres liés : chaque colonne de paramètre table peut spécifier ses données actuelles longueur, SQL_NULL_DATA ou il peut spécifier des données lors de l’exécution par le biais de sa mémoire tampon de longueur / d’indicateur. Colonne de paramètre table valeurs peuvent être passées par les appels répétés à SQLPutData comme d’habitude lorsqu’un caractère ou une valeur binaire doit être passée en fragments.  
  
 Une fois toutes les colonnes de paramètre table traitées, le pilote revient au paramètre table pour traiter d'autres lignes de données de paramètre table. Par conséquent, pour les paramètres table de données en cours d'exécution, le pilote ne suit pas l'analyse séquentielle habituelle des paramètres liés. Un paramètre table lié est interrogé jusqu'à ce que SQLPutData est appelée avec *StrLen_Or_IndPtr* égal à 0, moment auquel le pilote ignore les colonnes de paramètre table et se déplace vers le paramètre de procédure stockée réel suivant.  Lorsque SQLPutData transmet une valeur d’indicateur supérieure ou égale à 1, le pilote traite les lignes et colonnes de paramètre table séquentiellement jusqu'à ce qu’il comporte des valeurs pour toutes les lignes et colonnes liées. Le pilote revient ensuite au paramètre table. Entre recevoir le jeton pour le paramètre table à partir de SQLParamData et SQLPutData (hstmt, NULL, n) l’appel pour un paramètre table, l’application doit définir les données de colonne constitutifs de paramètre table et l’indicateur de contenu de la mémoire tampon pour le ou les lignes suivantes à passer au serveur.  
  
 Exemple de code pour ce scénario est dans la routine `demo_variable_TVP_binding` dans [utiliser les paramètres &#40;ODBC&#41;](../native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-from-the-system-catalog"></a>Récupération des métadonnées de paramètre table du catalogue système  
 Lorsqu’une application appelle SQLProcedureColumns pour une procédure qui possède des paramètres de paramètre table, DATA_TYPE est retourné comme SQL_SS_TABLE et TYPE_NAME est le nom du type de table pour le paramètre table. Deux colonnes supplémentaires sont ajoutées au jeu de résultats retourné par SQLProcedureColumns : SS_TYPE_CATALOG_NAME retourne le nom du catalogue où le type de table du paramètre de valeur de la table est défini et SS_TYPE_SCHEMA_NAME retourne le nom du schéma où le où le type de table du paramètre de valeur de la table est défini. Conformément à la spécification ODBC, SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMA_NAME apparaissent avant toutes les colonnes spécifiques au pilote qui ont été ajoutées dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et après toutes les colonnes mandatées par ODBC lui-même.  
  
 Les nouvelles colonnes seront remplies à la fois pour les paramètres table, mais aussi pour les paramètres du type CLR défini par l'utilisateur. Les colonnes de schéma et de catalogue existantes des paramètres définis par l'utilisateur continuent d'être remplies, mais le fait de disposer de colonnes de schéma et de catalogue communes pour les types de données qui en ont besoin simplifie le développement d'applications dans le futur. (Notez que les collections de schémas XML sont quelque peu différentes et ne sont pas incluses dans cette modification.)  
  
 Une application utilise SQLTables pour déterminer les noms des types de tables de la même manière que pour les tables persistantes, les tables système et les vues. Un nouveau type de table, TABLE TYPE, est introduit pour permettre à une application d'identifier les types de tables associés aux paramètres table. Les types de tables et les tables standard utilisent des espaces de noms différents. Cela signifie que vous pouvez utiliser le même nom pour un type de table et pour une table réelle. À cet effet, un nouvel attribut d'instruction, SQL_SOPT_SS_NAME_SCOPE, a été introduit. Cet attribut spécifie si SQLTables et autres fonctions de catalogue qui acceptent un nom de table en tant que paramètre doivent interpréter le nom de table en tant que le nom d’une table réelle ou le nom d’un type de table.  
  
 Une application utilise SQLColumns pour déterminer les colonnes d’un type de table de la même façon qu’il s’exécute pour les tables persistantes, mais que vous devez d’abord définir SQL_SOPT_SS_NAME_SCOPE pour indiquer qu’elle fonctionne avec les types de table plutôt que des tables réelles. SQLPrimaryKeys peut également être utilisé avec les types de tables, à l’aide de SQL_SOPT_SS_NAME_SCOPE.  
  
 Exemple de code pour ce scénario est dans la routine `demo_metadata_from_catalog_APIs` dans [utiliser les paramètres &#40;ODBC&#41;](../native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-for-a-prepared-statement"></a>Récupération des métadonnées de paramètre table pour une instruction préparée  
 Dans ce scénario, une application utilise SQLNumParameters et SQLDescribeParam pour récupérer des métadonnées pour les paramètres table.  
  
 Le champ IPD SQL_CA_SS_TYPE_NAME est utilisé pour récupérer le nom du type du paramètre table. Les champs IPD SQL_CA_SS_TYPE_SCHEMA_NAME et SQL_CA_SS_TYPE_CATALOG_NAME sont utilisés pour récupérer respectivement son catalogue et son schéma.  
  
 Les définitions de types de tables et les paramètres table doivent se trouver dans la même base de données. SQLSetDescField signalera une erreur si une application définit SQL_CA_SS_TYPE_CATALOG_NAME lors de l’utilisation des paramètres table.  
  
 SQL_CA_SS_TYPE_CATALOG_NAME et SQL_CA_SS_TYPE_SCHEMA_NAME peuvent également être utilisés pour récupérer le catalogue et le schéma associés aux paramètres du type CLR défini par l'utilisateur. SQL_CA_SS_TYPE_CATALOG_NAME et SQL_CA_SS_TYPE_SCHEMA_NAME sont des alternatives aux attributs existants de schéma de catalogue spécifiques au type pour les types CLR définis par l'utilisateur.  
  
 Une application utilise SQLColumns pour récupérer les métadonnées de colonne pour un paramètre table dans ce scénario, trop, comme SQLDescribeParam ne retourne pas de métadonnées pour les colonnes d’une colonne de paramètre table.  
  
 Exemple de code pour ce cas d’utilisation se trouve dans la routine `demo_metadata_from_prepared_statement` dans [utiliser les paramètres &#40;ODBC&#41;](../native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
