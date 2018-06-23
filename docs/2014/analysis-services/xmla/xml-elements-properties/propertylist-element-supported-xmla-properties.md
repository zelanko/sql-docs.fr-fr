---
title: Prise en charge des propriétés XMLA (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- properties [XML for Analysis]
- XML for Analysis, properties
- XMLA, properties
ms.assetid: 5745f7b4-6b96-44d5-b77c-f2831a898e5e
caps.latest.revision: 24
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 89293d101513cb2cec07fe69b2ba22e67f55dd21
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152020"
---
# <a name="supported-xmla-properties-xmla"></a>Propriétés XMLA prises en charge (XMLA)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge les propriétés répertoriées dans le tableau suivant. Vous utilisez ces propriétés dans le [propriétés](properties-element-xmla.md) élément de la [Discover](../xml-elements-methods-discover.md) et [Execute](../xml-elements-methods-execute.md) méthodes.  
  
|Nom   |Élément|  
|----------|-------------|  
|AxisFormat|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Détermine le format utilisé dans une [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) jeu de résultats pour décrire les axes du dataset multidimensionnel. Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*ClusterFormat*|Le `MDDataSet` axe est constitué d’un ou plusieurs [CrossProduct](crossproduct-element-xmla.md) éléments.|  
|*CustomFormat*|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilise le *TupleFormat* format de ce paramètre.|  
|*TupleFormat*|(Par défaut) Le `MDDataSet` axe contient un ou plusieurs [Tuple](tuple-element-xmla.md) éléments.|  
  
 Cette propriété peut s'utiliser avec la méthode `Execute`.  
  
|Nom   |Élément|  
|----------|-------------|  
|BeginRange|*Utilisation*<br /> Facultatif, en écriture seule `Integer` propriété<br /><br /> *Description*<br /> Contient une valeur entière de base zéro qui correspond à une valeur d'attribut `CellOrdinal`. (Le `CellOrdinal` attribut fait partie de la [cellule](cell-element-mddataset-xmla.md) élément dans le [CellData](celldata-element-xmla.md) section de `MDDataSet`.)<br /><br /> L'application cliente peut utiliser cette propriété conjointement avec la propriété `EndRange` pour restreindre un dataset OLAP retourné par une commande à une plage de cellules spécifique. Si -1 est spécifié, toutes les cellules jusqu'à la cellule spécifiée dans la propriété `EndRange` sont retournées.<br /><br /> La valeur par défaut de cette propriété est -1.<br /><br /> Cette propriété peut s'utiliser avec la méthode `Execute`.|  
|Catalogue|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Lors de l'établissement d'une session avec une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour envoyer une commande XMLA, cette propriété est équivalente à la propriété OLE DB DBPROP_INIT_CATALOG.<br /><br /> Lorsque vous la définissez au cours d'une session pour modifier la base de données actuelle de la session, cette propriété est équivalente à la propriété OLE DB DBPROP_CURRENTCATALOG.<br /><br /> La valeur par défaut de cette propriété est une chaîne vide.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|CatalogLocation|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_CATALOGLOCATION.<br /><br /> La valeur par défaut de cette propriété est zéro (0), ce qui équivaut à DBPROPVAL_CL_START.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|ClientProcessID|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Contient l'identificateur (ID) du thread de processus pour la session active.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|CommitTimeout|*Utilisation*<br /> Facultatif, en écriture seule `Integer` propriété<br /><br /> *Description*<br /> Détermine le délai d'attente, exprimé en secondes, observé dans la phase de validation d'une commande XMLA en cours d'exécution avant d'effectuer une restauration. La phase de validation correspond à des commandes XMLA telles que [instruction](../xml-elements-commands/statement-element-xmla.md) ou [processus](../xml-elements-commands/process-element-xmla.md).<br /><br /> Une valeur de zéro (0) indique que l'instance attend indéfiniment.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|Contenu|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Détermine le type des données retournées par les méthodes `Discover` et `Execute`. Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Aucun*|Permet de vérifier la structure de la commande sans l'exécuter.|  
|*Schéma*|Retourne le schéma XML relatif à la commande demandée. Le schéma XML précise les colonnes et fournit d'autres informations.|  
|*Données*|Retourne uniquement les données demandées.|  
|*SchemaData*|(Valeur par défaut) Retourne les informations du schéma et les données.|  
  
 Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.  
  
|Nom   |Élément|  
|----------|-------------|  
|Cube|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Contient le nom du cube qui définit le contexte de la commande. Si la commande elle-même contient un nom de cube, comme dans la clause FROM d’une expression multidimensionnelle (MDX) [sélectionnez](/sql/mdx/mdx-data-manipulation-select) instruction, le paramètre de cette propriété est ignorée.<br /><br /> La valeur par défaut de cette propriété est une chaîne vide.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DataSourceInfo|*Utilisation*<br /> Propriété `String` requise, en lecture/écriture<br /><br /> *Description*<br /> Contient les informations requises pour se connecter à la source de données, par exemple le nom de l'instance.<br /><br /> Les applications clientes ne doivent pas construire le contenu de la propriété `DataSourceInfo` à envoyer à une instance. Au lieu de cela, l’application cliente doit rechercher les sources de données pris en charge par le fournisseur à l’aide de la `Discover` pour récupérer le [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md) ensemble de lignes. L'application cliente renvoie ensuite pour la propriété `DataSourceInfo` la valeur que le client a extraite de l'ensemble de lignes DISCOVER_DATASOURCES.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropCatalogTerm|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_CATALOGTERM.<br /><br /> La valeur par défaut de cette propriété est « Database ».<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropCatalogUsage|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_CATALOGUSAGE.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropColumnDefinition|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_COLUMNDEFINITION.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropConcatNullBehavior|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_CONCATNULLBEHAVIOR.<br /><br /> La valeur par défaut de cette propriété est 1, ce qui équivaut à DBPROPVAL_CB_NULL.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropDataSourceReadOnly|*Utilisation*<br /> Facultatif, en lecture seule `Boolean` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_DATASOURCEREADONLY.<br /><br /> La valeur par défaut de cette propriété est FALSE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropGroupBy|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_GROUPBY.<br /><br /> La valeur par défaut de cette propriété est 2, ce qui équivaut à DBPROPVAL_GB_EQUALS_SELECT.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropHeterogeneousTables|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_HETEROGENEOUSTABLES.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropIdentifierCase|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_IDENTIFIERCASE.<br /><br /> La valeur par défaut de cette propriété est 8, ce qui équivaut à DBPROPVAL_IC_MIXED.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropInitMode|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_INIT_MODE.<br /><br /> Les seules valeurs prises en charge pour cette propriété sont DB_MODE_READWRITE et DB_MODE_READ.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMaxIndexSize|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_MAXINDEXSIZE.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMaxOpenChapters|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_MAXOPENCHAPTERS.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMaxRowSize|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_MAXROWSIZE.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMaxRowSizeIncludeBlob|*Utilisation*<br /> Propriété `Boolean` facultative, en lecture seule<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_MAXROWSIZEINCLUDESBLOB.<br /><br /> La valeur par défaut de cette propriété est TRUE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMaxTablesInSelect|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_MAXTABLESINSELECT.<br /><br /> La valeur par défaut de cette propriété est 1.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdAutoexists|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Détermine le comportement de la fonctionnalité autoexist. Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|Valeur par défaut, égale à 1.|  
|*1*|Applique les fonctionnalités autoexist profondes pour les axes de requête et les jeux nommés. Inclut des clauses WHERE et des instructions de sous-sélection.|  
|*2*|Applique les fonctionnalités autoexist profondes pour les axes de requête et exclut les jeux nommés des fonctionnalités autoexist. Inclut des clauses WHERE et des instructions de sous-sélection.|  
|*3*|N'applique aucune fonctionnalité autoexist pour les jeux nommés avec la clause WHERE. Applique des fonctionnalités autoexist superficielles pour les axes de requête avec la clause WHERE. Applique des fonctionnalités autoexist profondes pour les axes de requête avec des instructions de sous-sélection et pour les jeux nommés avec des instructions de sous-sélection.|  
  
 Les valeurs par défaut de cette propriété sont zéro ou vide. Il s'agit d'une propriété de session qui ne peut être définie que lors de la création de la session.  
  
|Nom   |Élément|  
|----------|-------------|  
|DbpropMsmdCacheMode|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdCachePolicy|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdCacheRatio|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdCacheRatio2|*Utilisation*<br /> Facultatif, en lecture/écriture `Double` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdCompareCaseNotSensitiveStringFlags|*Utilisation*<br /> Propriété `Integer` facultative, en lecture/écriture<br /><br /> *Description*<br /> Détermine une comparaison des chaînes respectant la casse et des fonctionnalités d'ordre de tri. Cette propriété précise les modalités selon lesquelles les comparaisons s'effectuent dans les jeux de caractères qui ne prennent pas en charge les majuscules et les minuscules, par exemple le katakana pour le japonais et l'hindi. La valeur de cette propriété est définie dans la première connexion du thread de processus et affecte toutes les connexions suivantes dans ce thread de processus.<br /><br /> Utilisez le tableau suivant pour déterminer les indicateurs à utiliser.|  
  
|Nom   |Valeur|Description|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0 x 00000001*|La casse est ignorée.|  
|Non applicable|*0 x 00000002*|Comparaison binaire. Les caractères sont comparés en fonction de leur valeur sous-jacente dans le jeu de caractères et non selon leur ordre dans leur alphabet particulier.|  
|NORM_IGNORENONSPACE|*0 x 00000010*|Les caractères sans espace sont ignorés.|  
|NORM_IGNORESYMBOLS|*0 x 00000100*|Les symboles sont ignorés.|  
|NORM_IGNOREKANATYPE|*0 x 00001000*|Aucune distinction n'est faite entre les caractères japonais hiragana et katakana. Lors des comparaisons, les caractères hiragana et katakana correspondants sont considérés comme égaux.|  
|NORM_IGNOREWIDTH|*0 x 00010000*|Aucune distinction n'est faite entre les versions du même caractère codées sur un octet et sur deux octets.|  
|SORT_STRINGSORT|*0 x 00100000*|La ponctuation est traitée de la même façon que les symboles.|  
  
 Pour plus d'informations sur la comparaison de chaînes dans OLE DB, recherchez « CompareString » dans la section Platform SDK de MSDN Library (en anglais).  
  
 Il n’existe aucune valeur par défaut de cette propriété.  
  
 Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.  
  
|Nom   |Élément|  
|----------|-------------|  
|DbpropMsmdCompareCaseSensitiveStringFlags|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Détermine une comparaison de chaînes ne respectant pas la casse et des fonctionnalités d'ordre de tri. Cette propriété précise les modalités selon lesquelles les comparaisons s'effectuent dans les jeux de caractères qui ne prennent pas en charge les majuscules et les minuscules, par exemple le katakana pour le japonais et l'hindi. La valeur de cette propriété est définie dans la première connexion du thread de processus et affecte toutes les connexions suivantes dans ce thread de processus.<br /><br /> Utilisez le tableau suivant pour déterminer les indicateurs à utiliser.|  
  
|Nom   |Valeur|Description|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0 x 00000001*|La casse est ignorée.|  
|Non applicable|*0 x 00000002*|Comparaison binaire. Les caractères sont comparés en fonction de leur valeur sous-jacente dans le jeu de caractères et non selon leur ordre dans leur alphabet particulier.|  
|NORM_IGNORENONSPACE|*0 x 00000010*|Les caractères sans espace sont ignorés.|  
|NORM_IGNORESYMBOLS|*0 x 00000100*|Les symboles sont ignorés.|  
|NORM_IGNOREKANATYPE|*0 x 00001000*|Aucune distinction n'est faite entre les caractères japonais hiragana et katakana. Lors des comparaisons, les caractères hiragana et katakana correspondants sont considérés comme égaux.|  
|NORM_IGNOREWIDTH|*0 x 00010000*|Aucune distinction n'est faite entre les versions du même caractère codées sur un octet et sur deux octets.|  
|SORT_STRINGSORT|*0 x 00100000*|La ponctuation est traitée de la même façon que les symboles.|  
  
 Pour plus d'informations sur la comparaison de chaînes dans OLE DB, recherchez « CompareString » dans la section Platform SDK de MSDN Library (en anglais).  
  
 Il n’existe aucune valeur par défaut de cette propriété.  
  
 Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.  
  
|Nom   |Élément|  
|----------|-------------|  
|DbpropMsmdDebugMode|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdDynamicDebugLimit|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdFlattened2|*Utilisation*<br /> Facultatif, en lecture/écriture `Boolean` propriété<br /><br /> *Description*<br /> Fournit tous les membres d'une hiérarchie parent-enfant dans une seule colonne de table dans le résultat aplati, sauf si la hiérarchie parent-enfant est demandée sur l'axe 0. Le modèle de niveau pour les colonnes de sortie n'est pas utilisé.<br /><br /> La valeur par défaut de cette propriété est FALSE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdMDXCompatibility|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Détermine comment les membres d'espace réservé d'une hiérarchie déséquilibrée sont traités. Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|Pour assurer la compatibilité avec les versions antérieures de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], cette valeur est équivalente à 1|  
|*1*|Les hiérarchies dans les dimensions de rôle actif reçoivent une légende qui contient le nom de dimension et le nom de hiérarchie. La légende a le format suivant :<br /><br /> [Dimension].[Hiérarchie]<br /><br /> Les membres d'espace réservé sont exposés.|  
|*2*|Les hiérarchies dans les dimensions de rôle actif reçoivent une légende qui contient le nom de dimension et le nom de hiérarchie. La légende a le format suivant :<br /><br /> [Dimension].[Hiérarchie]<br /><br /> Les membres d'espace réservé ne sont pas exposés.|  
|*3*|(Valeur par défaut) Les membres d'espace réservé ne sont pas exposés.|  
  
 Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.  
  
|Nom   |Élément|  
|----------|-------------|  
|DbpropMsmdMDXUniqueNameStyle|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Détermine l'algorithme employé pour générer les noms uniques des membres dans une dimension. Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.<br /><br /> La valeur par défaut de cette propriété est 6.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|Pour assurer la compatibilité avec les versions antérieures de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], cette valeur est équivalente à 2.|  
|*1*|Utilise un algorithme générant des chemins d'accès basés sur les clés :<br /><br /> [dim].&[clé1].&[clé2]|  
|*2*|Utilise un algorithme générant des chemins d'accès basés sur les noms :<br /><br /> [dim].[nom1].&[nom2]|  
|*3*|Utilise des noms dont l'unicité est garantie et qui ne changent pas dans le temps.|  
  
 Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.  
  
|Nom   |Élément|  
|----------|-------------|  
|DbpropMsmdSQLCompatibility|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMsmdSubQueries|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Masque de bits qui détermine le comportement des sous-requêtes. Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|Valeur par défaut, compatible avec les versions antérieures de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Les membres calculés ou ensembles calculés ne sont pas autorisés dans les sous-sélections ou les sous-cubes.|  
|*1*|Les membres calculés ou ensembles calculés sont autorisés dans les sous-sélections ou les sous-cubes. Les ascendants du membre calculé ne sont pas inclus dans l'espace de la sous-sélection ou du sous-cube.|  
|*2*|Les membres calculés ou ensembles calculés sont autorisés dans les sous-sélections ou les sous-cubes. Les ascendants du membre calculé sont inclus dans l'espace de la sous-sélection ou du sous-cube.|  
  
 Les valeurs par défaut de cette propriété sont zéro ou vide.  
  
 Il s'agit d'une propriété de session qui ne peut être définie que lors de la création de la session.  
  
 Consultez [des membres calculés dans les sous-sélections et les sous-cubes](../../multidimensional-models/mdx/calculated-members-in-subselects-and-subcubes.md) pour une explication détaillée du comportement de membres calculés ou ensembles calculés dans les sous-sélections et les sous-cubes.  
  
|Nom   |Élément|  
|----------|-------------|  
|DbpropMsmdUseFormulaCache|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropMultiTableUpdate|*Utilisation*<br /> Facultatif, en lecture seule `Boolean` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_MULTITABLEUPDATE.<br /><br /> La valeur par défaut de cette propriété est FALSE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropNullCollation|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_NULLCOLLATION.<br /><br /> La valeur par défaut de cette propriété est 4, ce qui équivaut à DBPROPVAL_NC_LOW.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropOrderByColumnsInSelect|*Utilisation*<br /> Facultatif, en lecture seule `Boolean` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_ORDERBYCOLUMNSINSELECT.<br /><br /> La valeur par défaut de cette propriété est FALSE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropOutputParameterAvailable|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_OUTPUTPARAMETERAVAILABILITY.<br /><br /> La valeur par défaut de cette propriété est 1, ce qui équivaut à DBPROPVAL_OA_NOTSUPPORTED.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropPersistentIdType|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_PERSISTENTIDTYPE.<br /><br /> La valeur par défaut de cette propriété est 4, ce qui équivaut à DBPROPVAL_PT_NAME.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropPrepareAbortBehavior|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_PREPAREABORTBEHAVIOR.<br /><br /> La valeur par défaut de cette propriété est 1, ce qui équivaut à DBPROPVAL_CB_DELETE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropPrepareCommitBehavior|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_PREPARECOMMITBEHAVIOR.<br /><br /> La valeur par défaut de cette propriété est 1, ce qui équivaut à DBPROPVAL_CB_DELETE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropProcedureTerm|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_PROCEDURETERM.<br /><br /> La valeur par défaut de cette propriété est « Calculated member ».<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropQuotedIdentifierCase|*Utilisation*<br /> Propriété `Integer` facultative, en lecture seule<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_QUOTEDIDENTIFIERCASE.<br /><br /> La valeur par défaut de cette propriété est 8, ce qui équivaut à DBPROPVAL_IC_MIXED.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropSchemaUsage|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_SCHEMAUSAGE.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropSqlSupport|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_SQLSUPPORT.<br /><br /> La valeur par défaut de cette propriété est 512, ce qui équivaut à DBPROPVAL_SQL_SUBMINIMUM.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropSubqueries|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_SUBQUERIES.<br /><br /> **Remarque** Alors que le langage DMX (Data Mining Extensions) prend en charge les sous-requêtes, cette propriété fait référence à la prise en charge des sous-requêtes dans SQL.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropSupportedTxnDdl|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_SUPPORTEDTXNDDL.<br /><br /> La valeur par défaut de cette propriété est zéro (0), ce qui équivaut à DBPROPVAL_TC_NONE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropSupportedTxnIsoLevels|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_SUPPORTEDTXNISOLEVELS.<br /><br /> La valeur par défaut de cette propriété est 4096, ce qui équivaut à DBPROPVAL_TI_READCOMMITTED.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropSupportedTxnIsoRetain|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_SUPPORTEDTXNISORETAIN.<br /><br /> La valeur par défaut de cette propriété est 292, ce qui équivaut à une combinaison de DBPROPVAL_TR_ABORT_NO, DBPROPVAL_TR_COMMIT_NO et DBPROPVAL_TR_NONE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|DbpropTableTerm|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_TABLETERM.<br /><br /> La valeur par défaut de cette propriété est « Cube ».<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|Dialect|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Établit le dialecte utilisé dans les situations suivantes :<br /><br /> -Le dialecte que le fournisseur utilise la première fois que le fournisseur essaie d’exécuter une requête.<br />-Le dialecte utilisé pour les erreurs d’exécution retournées comme résultat d’échecs de requêtes.<br /><br /> Vous pouvez utiliser la propriété `Dialect` lorsque vous vous attendez à ce que la plupart des requêtes utilisent un dialecte particulier plutôt que les autres.<br /><br /> La syntaxe de requête peut être semblable dans les dialectes des langages tels que DMX et SQL. C'est pourquoi il est possible que [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ne soit pas en mesure d'inférer le dialecte de la syntaxe de requête. Si une requête ne fonctionne pas dans un dialecte, l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] peut essayer d'exécuter à nouveau cette requête dans un dialecte différent.<br /><br /> Si la propriété `Dialect` est définie, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne les erreurs d'exécution de la requête dans le dialecte qui a la priorité, même si le fournisseur essaie de réexécuter la requête dans un autre dialecte. Supposons par exemple que la propriété `Dialect` ait la valeur MDGUID_DM. Le fournisseur essaie d'abord d'exécuter la requête comme une requête d'exploration de données, mais cette tentative échoue. Ensuite, le fournisseur soumet à nouveau la requête, cette fois en tant que requête SQL. Toutefois, cette requête SQL échoue également. Comme la valeur de la propriété `Dialect` est MDGUID_DM, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne un message d'erreur d'exploration de données et non un message d'erreur SQL.<br /><br /> Si la propriété `Dialect` n'est pas définie, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne les erreurs d'exécution de la requête dans le dialecte utilisé en dernier. Supposons par exemple qu'une requête d'exploration de données échoue alors que la propriété `Dialect` n'est pas définie. Ensuite, le fournisseur soumet à nouveau la requête, en tant que requête SQL. La requête SQL échoue également. Comme la propriété `Dialect` n'est pas définie, le fournisseur retourne alors un message d'erreur SQL et non un message d'erreur d'exploration de données.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.<br /><br /> Les dialectes disponibles pour cette propriété sont répertoriés dans le tableau suivant.|  
  
|Nom   |Valeur|Description|  
|----------|-----------|-----------------|  
|DBGUID_SQL|*C8B522D7-5CF3-11CE-ADE5-00AA0044773D*|L'analyseur SQL a la priorité.|  
|MDGUID_DM|*62C58FED-CCA5-44F1-83B6-7B45682B3904*|L'analyseur DMX a la priorité.|  
|MDGUID_MDX|*A07CCCD0-8148-11D0-87BB-00C04FC33942*|L'analyseur MDX a la priorité.|  
  
|Nom   |Élément|  
|----------|-------------|  
|Désactiver les faits de prérécupération|*Utilisation*<br /> Propriété `Boolean` facultative, en lecture/écriture,<br /><br /> *Description*<br /> En cas de définition sur la valeur True, le moteur cesse toute tentative de prérécupération des valeurs pour la longueur de la session.<br /><br /> La valeur par défaut de cette propriété est `False`.|  
|EffectiveRoles|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|EffectiveUserName|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Spécifie le nom d'un compte à utiliser pour remplacer le nom d'utilisateur lors de la connexion à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. La valeur de la propriété n’est pas normalisé, qui l’expression MDX [nom d’utilisateur](/sql/mdx/username-mdx) fonction retourne la valeur littérale si cette propriété est utilisée. Cette propriété peut être utilisée uniquement par les administrateurs de serveur.<br /><br /> Cette propriété prend en charge les types SID suivants : User, Group, Alias, WellKnownGroup et Computer.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|EndRange|*Utilisation*<br /> Facultatif, en écriture seule `Integer` propriété<br /><br /> *Description*<br /> Spécifie une valeur entière de base zéro qui correspond à une valeur d'attribut `CellOrdinal`. (L'attribut `CellOrdinal` fait partie de l'élément `Cell` dans la section `CellData` de `MDDataSet`.)<br /><br /> L'application cliente peut utiliser cette propriété conjointement avec la propriété `BeginRange` pour restreindre un dataset OLAP retourné par une commande à une plage de cellules spécifique. Si -1 est spécifié, toutes les cellules à partir de la cellule spécifiée dans la propriété `BeginRange` sont retournées.<br /><br /> La valeur par défaut de cette propriété est -1.<br /><br /> Cette propriété peut s'utiliser avec la méthode `Execute`.|  
|ExecutionMode|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> La valeur par défaut de cette propriété est *Execute*.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|ForceCommitTimeout|*Utilisation*<br /> Facultatif, en écriture seule `Integer` propriété<br /><br /> *Description*<br /> Détermine le délai d'attente, exprimé en secondes, observé dans la phase de validation d'une commande XMLA en cours d'exécution avant de forcer les commandes soumises antérieurement à effectuer une restauration. La phase de validation correspond à des commandes XMLA telles que `Statement` ou `Process`.<br /><br /> Une valeur de zéro (0) indique que l'instance attend indéfiniment.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|Format|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Détermine le type d'ensemble de résultats retourné par les méthodes `Discover` et `Execute`. Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
 La valeur par défaut de cette propriété est *natif*.  
  
 Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Sous forme de tableau*|Retourne un résultat à l’aide de la [ensemble de lignes](../xml-data-types/rowset-data-type-xmla.md) type de données.|  
|*Multidimensionnel*|Retourne un ensemble de lignes à l’aide de la [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) type de données.|  
|*Natif*|Aucun format n'est spécifié explicitement. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] retourne le format approprié pour la commande. Le type de résultat réel est identifié par l'espace de noms du résultat.|  
  
|Nom   |Élément|  
|----------|-------------|  
|ImpactAnalysis|*Utilisation*<br /> Facultatif, en écriture seule `Boolean` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|LocaleIdentifier|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Lit ou définit l'identificateur de paramètres régionaux (LCID) utilisé par la méthode `Discover` ou `Execute`. Pour accéder à une liste hexadécimale complète des identificateurs de langue, recherchez « Language Identifiers » dans MSDN Library.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MaximumRows|*Utilisation*<br /> Facultatif, en écriture seule `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropAggregateCellUpdate|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_AGGREGATECELL_UPDATE.<br /><br /> La valeur par défaut de cette propriété est 4, ce qui équivaut à MDPROPVAL_AU_SUPPORTED.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropAxes|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_AXES.<br /><br /> La valeur par défaut de cette propriété est de 2147483647.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropDrillFunctions|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Détermine le niveau de support pour les fonctions d'extraction sur le serveur. Les valeurs suivantes sont utilisées pour générer un masque de bits valide :<br /><br /> MDPROPVAL_MDF_BASIC (0x01)<br /><br /> MDPROPVAL_MDF_ASYMMETRIC (0x02)<br /><br /> MDPROPVAL_MDF_CALC_MEMBERS (0x04)<br /><br /> Les valeurs par défaut sont :<br /><br /> 3 pour SQL Server 2008<br /><br /> 7 pour SQL Server 2008 R2 et [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropFlatteningSupport|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_FLATTENING_SUPPORT.<br /><br /> La valeur par défaut de cette propriété est 1, ce qui équivaut à MDPROPVAL_FS_FULL_SUPPORT.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxCaseSupport|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_CASESUPPORT.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxDescFlags|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_DESCFLAGS.<br /><br /> La valeur par défaut de cette propriété est 7, ce qui équivaut à MDPROPVAL_MD_BEFORE, MDPROPVAL_MD_AFTER et MDPROPVAL_MD_SELF.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxFormulas|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_FORMULAS.<br /><br /> La valeur par défaut de cette propriété est 63, ce qui équivaut à une combinaison de MDPROPVAL_MF_WITH_CALCMEMBERS, MDPROPVAL_MF_WITH_NAMEDSETS, MDPROPVAL_MF_CREATE_CALCMEMBERS, MDPROPVAL_MF_CREATE_NAMEDSETS, MDPROPVAL_MF_SCOPE_SESSION et MDPROPVAL_MF_SCOPE_GLOBAL.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxJoinCubes|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_JOINCUBES.<br /><br /> La valeur par défaut de cette propriété est 1, ce qui équivaut à MDPROPVAL_MJC_SINGLECUBE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxMemberFunctions|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_MEMBER_FUNCTIONS.<br /><br /> La valeur par défaut de cette propriété est 15, ce qui équivaut à une combinaison de toutes les valeurs OLE DB disponibles.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxNamedSets|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Masque de bits provenant de valeurs répertoriées dans la table suivante.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0 x 01*|MDPROPVAL_MNS_BASIC.|  
|*0 x 02*|MDPROPVAL_MNS_DYNAMIC.|  
|*0 x 04*|MDPROPVAL_MNS_DISPLAYFOLDER.|  
|*0 x 08*|MDPROPVAL_MNS_CAPTION.|  
  
 Cette propriété a pour valeur par défaut 15.  
  
|Nom   |Élément|  
|----------|-------------|  
|MdpropMdxNonMeasureExpressions|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_NONMEASURE_EXPRESSIONS.<br /><br /> La valeur par défaut de cette propriété est zéro (0), ce qui équivaut à MDPROPVAL_NME_ALLDIMENSIONS.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxNumericFunctions|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_NUMERIC_FUNCTIONS.<br /><br /> La valeur par défaut de cette propriété est 2047, ce qui équivaut à une combinaison de MDPROPVAL_MNF_MEDIAN, MDPROPVAL_MNF_VAR, MDPROPVAL_MNF_STDDEV, MDPROPVAL_MNF_RANK, MDPROPVAL_MNF_AGGREGATE, MDPROPVAL_MNF_COVARIANCE, MDPROPVAL_MNF_CORRELATION, MDPROPVAL_MNF_LINREGSLOPE, MDPROPVAL_MNF_LINREGVARIANCE, MDPROPVAL_MNF_LINREG2 et MDPROPVAL_MNF_LINREGPOINT.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxObjQualification|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_OBJQUALIFICATION.<br /><br /> La valeur par défaut de cette propriété est 496, ce qui équivaut à une combinaison de MDPROPVAL_MOQ_DIM_HIER, MDPROPVAL_MOQ_DIMHIER_LEVEL, MDPROPVAL_MOQ_DIMHIER_MEMBER, MDPROPVAL_MOQ_LEVEL_MEMBER et MDPROPVAL_MOQ_MEMBER_MEMBER.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxOuterReference|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_OUTERREFERENCE.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxQueryByProperty|*Utilisation*<br /> Facultatif, en lecture seule `Boolean` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_QUERYBYPROPERTY.<br /><br /> La valeur par défaut de cette propriété est TRUE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxRangeRowset|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_RANGEROWSET.<br /><br /> La valeur par défaut de cette propriété est 4, ce qui équivaut à MDPROPVAL_RR_UPDATE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxSetFunctions|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_SET_FUNCTIONS.<br /><br /> La valeur par défaut de cette propriété est 524287, ce qui équivaut à une combinaison de MDPROPVAL_MSF_TOPPERCENT, MDPROPVAL_MSF_BOTTOMPERCENT, MDPROPVAL_MSF_TOPSUM, MDPROPVAL_MSF_BOTTOMSUM, MDPROPVAL_MSF_PERIODSTODATE, MDPROPVAL_MSF_LASTPERIODS, MDPROPVAL_MSF_YTD, MDPROPVAL_MSF_QTD, MDPROPVAL_MSF_MTD, MDPROPVAL_MSF_WTD, MDPROPVAL_MSF_DRILLDOWNMEMBER, MDPROPVAL_MSF_DRILLDOWNLEVEL, MDPROPVAL_MSF_DRILLDOWNMEMBERTOP, MDPROPVAL_MSF_DRILLDOWNMEMBERBOTTOM, MDPROPVAL_MSF_DRILLDOWNLEVEL, MDPROPVAL_MSF_DRILLDOWNLEVELTOP, MDPROPVAL_MSF_DRILLDOWNLEVELBOTTOM, MDPROPVAL_MSF_DRILLUPMEMBER, MDPROPVAL_MSF_DRILLUPLEVEL et MDPROPVAL_MSF_TOGGLEDRILLSTATE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxSlicer|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_SLICER.<br /><br /> La valeur par défaut de cette propriété est 2, ce qui équivaut à MDPROPVAL_MS_SINGLETUPLE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxStringCompop|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_MDX_STRING_COMPOP.<br /><br /> La valeur par défaut de cette propriété est 15, ce qui équivaut à une combinaison de MDPROPVAL_MSC_LESSTHAN, MDPROPVAL_MSC_GREATERTHAN, MDPROPVAL_MSC_LESSTHANEQUAL et MDPROPVAL_MSC_GREATERTHANEQUAL.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdpropMdxSubQueries|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété a pour valeur par défaut 63 dans SQL Server 2014.<br /><br /> Cette propriété a pour valeur par défaut 31 dans SQL Server 2008 R2 et [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<br /><br /> Cette propriété a pour valeur par défaut 15 dans SQL Server 2008<br /><br /> Indique le niveau de support pour les sous-requêtes dans MDX. Masque de bits provenant de valeurs répertoriées dans la table suivante.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0 x 01*|MDPROPVAL_MSQ_BASIC.|  
|*0 x 02*|MDPROPVAL_MSQ_ARBITRARYSHAPE.|  
|*0 x 04*|MDPROPVAL_MSQ_NONVISUAL.|  
|*0 x 08*|MDPROPVAL_MSQ_CALCMEMBERS.|  
  
|||  
|-|-|  
|*0 x 10*|MDPROPVAL_MSQ_CALCMEMBERS2|  
  
|Nom   |Élément|  
|----------|-------------|  
|MdpropNamedLevels|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_NAMED_LEVELS.<br /><br /> La valeur par défaut de cette propriété est 3, ce qui équivaut à une combinaison de MDPROPVAL_NL_NAMEDLEVELS et MDPROPVAL_NL_NUMBEREDLEVELS.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|MdxMissingMemberMode|*Utilisation*<br /> Facultatif, en écriture seule `String` propriété<br /><br /> *Description*<br /> Indique si les membres manquants sont ignorés dans les instructions MDX.<br /><br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_MDX_MISSING_MEMBER_MODE.<br /><br /> La valeur par défaut de cette propriété est *par défaut*.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.<br /><br /> Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Par défaut*|La valeur générée par l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est utilisée.|  
|*Erreur*|Génère une erreur.|  
|*Ignorer*|Les membres manquants sont toujours ignorés.|  
  
|Nom   |Élément|  
|----------|-------------|  
|MDXSupport|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Spécifie une énumération qui décrit le degré de prise en charge MDX.<br /><br /> `Value` = *Core* options MDX tous sont pris en charge.<br /><br /> Actuellement, la seule valeur de l’énumération contient est *Core*. Dans les versions ultérieures, d'autres valeurs seront définies pour cette énumération.<br /><br /> La valeur par défaut de cette propriété est *Core*.<br /><br /> Cette propriété peut s'utiliser avec la méthode `Discover`.|  
|NonEmptyThreshold|*Utilisation*<br /> Propriété `Integer` facultative, en lecture/écriture<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|Mot de passe|**Cette propriété n’est plus pris en charge.**<br /><br /> *Utilisation*<br /> Propriété `String` facultative, en écriture seule<br /><br /> *Description*<br /> Pour assurer la compatibilité descendante, cette propriété est ignorée et ne génère pas d'erreur lorsqu'elle est utilisée avec la méthode `Execute` ou `Discover`.|  
|ProviderName|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_DBMSNAME.<br /><br /> La valeur par défaut de cette propriété est « OLAP Server ».<br /><br /> Cette propriété peut s'utiliser avec la méthode `Discover`.|  
|ProviderType|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_DATASOURCE_TYPE.<br /><br /> La valeur par défaut de cette propriété est 6.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|ProviderVersion|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_DBMSVER.<br /><br /> La valeur par défaut de cette propriété est la version de l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Cette propriété peut s'utiliser avec la méthode `Discover`.|  
|ReadOnlySession|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|RealTimeOlap|*Utilisation*<br /> Facultatif, en lecture/écriture `Boolean` propriété<br /><br /> *Description*<br /> Lorsque cette propriété est spécifiée avec la valeur TRUE, toutes les partitions à l'écoute des notifications de table doivent être interrogées en temps réel, sans mise en cache préalable. Cette propriété est équivalente à la propriété OLE DB DBPROP_MSMD_REAL_TIME_OLAP.<br /><br /> La valeur par défaut de cette propriété est FALSE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|ReturnCellProperties|*Utilisation*<br /> Facultatif, en lecture/écriture `Boolean` propriété<br /><br /> *Description*<br /> La valeur par défaut de cette propriété est FALSE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|Rôles|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Spécifie une chaîne délimitée par des virgules contenant les noms de rôle sous lesquels une application cliente se connecte à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Cette propriété permet à l'utilisateur de se connecter en employant un rôle différent de son rôle actuel. Par exemple, un administrateur de serveur peut souhaiter se connecter à un cube en tant que membre d'un rôle afin de tester les autorisations accordées à ce rôle. Cet utilisateur doit être un membre du rôle spécifié pour pouvoir se connecter à l'aide de cette propriété.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.<br /><br /> **Remarque** Les noms de rôle respectent la casse. **N’utilisez pas** espaces entre les noms de rôle de délimitée par des virgules. Autrement, les requêtes portant sur des ensembles de cellules protégées risquent de retourner des erreurs et des résultats inattendus.|  
|SafetyOptions|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Détermine si les bibliothèques potentiellement dangereuses peuvent être enregistrées et chargées par les applications clientes.<br /><br /> La valeur de cette propriété détermine également si le mot clé PASSTHROUGH est autorisé dans les cubes locaux. Une erreur se produit dans les cas de figure suivants :<br /><br /> -Si une application cliente tente de créer un cube local avec une instruction INSERT INTO qui contient le mot clé PASSTHROUGH.<br />-Si une application cliente tente de mettre à jour un cube local qui contient une instruction INSERT INTO qui utilise le mot clé PASSTHROUGH.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.<br /><br /> Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Nom   |Valeur|Description|  
|----------|-----------|-----------------|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_DEFAULT|*0*|Cette valeur est traitée comme DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE.<br /><br /> Pour les connexions à un cube local, cette valeur dépend de l'utilisation de la propriété de chaîne de connexion CREATECUBE. Si la propriété de chaîne de connexion CREATECUBE est utilisée, cette valeur est équivalente à DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL. Autrement, cette valeur est équivalente à DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE.|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL|*1*|Cette valeur active toutes les bibliothèques de fonctions définies par l'utilisateur sans vérifier qu'il est possible de les utiliser en toute sécurité pour l'initialisation et dans des scripts. Pour les connexions à des cubes locaux, cette valeur permet l'utilisation de procédures stockées et du mot clé PASSTHROUGH dans les instructions INSERT INTO.<br /><br /> **Nous ne recommandons pas cette option**.|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE|*2*|Cette valeur vérifie que toutes les classes pour une bibliothèque de fonctions définies par l'utilisateur particulière sont contrôlées de sorte qu'il est possible de les utiliser en toute sécurité pour l'initialisation et dans des scripts. Pour les connexions à des cubes locaux, cette valeur empêche l'utilisation du mot clé PASSTHROUGH dans les instructions INSERT INTO et celle des procédures stockées dont la propriété PermissionSet n'a pas la valeur Safe.<br /><br /> Cette valeur supprime également les actions dans le [MDSCHEMA_ACTIONS](../../schema-rowsets/ole-db-olap/mdschema-actions-rowset.md) ou qui ont une valeur de code HTML ou commande dans la colonne ACTION_TYPE ont une valeur de l’URL dans la colonne ACTION_TYPE et une valeur dans la colonne de contenu qui n’effectue pas de lignes du schéma commencer par « http:// » ou « https:// ».|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_NONE|*3*|Cette valeur empêche l'utilisation des fonctions définies par l'utilisateur pendant la session. Pour les connexions à des cubes locaux, cette valeur empêche l'utilisation de toutes les procédures stockées et du mot clé PASSTHROUGH dans les instructions INSERT INTO.<br /><br /> Cette valeur supprime également toutes les actions de l'ensemble de lignes de schéma MDSCHEMA_ACTIONS.|  
  
|Nom   |Élément|  
|----------|-------------|  
|SecuredCellValue|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Spécifie le code d'erreur et les valeurs des propriétés de cellule `Value` et `Formatted Value` à retourner lors d'une tentative d'accès à une cellule protégée.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.<br /><br /> Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|(Par défaut) Pour la compatibilité avec les versions antérieures, cette valeur est identique à *1*. La signification de cette valeur par défaut peut faire l'objet de modifications dans les futures versions.|  
|*1*|Retourne : HRESULT = NO_ERROR<br /><br /> La propriété `Value` de la cellule contient le résultat sous la forme d'un type de données Variant. La chaîne « #N/A » est retournée dans la propriété `Formatted Value`.|  
|*2*|Retourne une erreur comme valeur de HRESULT.|  
|*3*|Retourne NULL dans les propriétés `Value` et `Formatted Value`.|  
|*4*|Retourne un zéro numérique (0) dans la propriété `Value` et un zéro mis en forme dans la propriété `Formatted Value`. Par exemple, 0.00 est retourné dans la propriété `Formatted Value` pour une cellule dont la propriété `Format` est « #. ## ».|  
|*5*|Retourne la chaîne « #SEC » dans les propriétés `Value` et `Formatted Value`.|  
  
|Nom   |Élément|  
|----------|-------------|  
|ServerName|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB DBPROP_SERVERNAME.<br /><br /> La valeur par défaut de cette propriété est le nom de l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|ShowHiddenCubes|*Utilisation*<br /> Facultatif, en lecture/écriture `Boolean` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> La valeur par défaut de cette propriété est FALSE.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|SQLQueryMode|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Détermine si les calculs sont inclus dans les requêtes SQL.<br /><br /> La valeur par défaut de cette propriété est *calculé*.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.<br /><br /> Cette propriété peut adopter l'une des valeurs répertoriées dans le tableau suivant.|  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Données*|Aucun calcul n'est inclus.|  
|*Calculé*|Les calculs sont retournés.|  
|*IncludeEmpty*|Les calculs et les lignes vides sont retournés.|  
  
|Nom   |Élément|  
|----------|-------------|  
|SQLSupport|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> La valeur par défaut de cette propriété est 512.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|SspropInitAppName|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Contient le nom de l'application cliente.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|SspropInitPacketsize|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Contient l'identificateur de l'application cliente.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|SspropInitWsid|*Utilisation*<br /> Facultatif, en lecture/écriture `String` propriété<br /><br /> *Description*<br /> Contient l'identificateur de la station de travail cliente.<br /><br /> Il n’existe aucune valeur par défaut de cette propriété.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|StateSupport|*Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Spécifie le degré de prise en charge de la conservation de l'état.<br /><br /> *Aucun* = <br />                        L'état n'est pas conservé.<br /><br /> *Sessions* = prise en charge de session est conservé.<br /><br /> Pour plus d’informations sur la conservation de l’état et la prise en charge de session, consultez [gestion des connexions et Sessions &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).<br /><br /> La valeur par défaut de cette propriété est *Sessions*.<br /><br /> Cette propriété peut s'utiliser avec la méthode `Discover`.|  
|Délai d'expiration|*Utilisation*<br /> Facultatif, en lecture/écriture `Integer` propriété<br /><br /> *Description*<br /> Spécifie le temps maximal, exprimé en secondes, pendant lequel l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] doit attendre qu'une requête réussisse avant de retourner une erreur. De même que la propriété de chaîne de connexion Writeback Timeout, cette propriété détermine également le temps maximal pendant lequel l'instance doit attendre qu'une mise à jour d'une table d'écriture différée réussisse avant de retourner une erreur.<br /><br /> La valeur par défaut de cette propriété est zéro (0).<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|TransactionDDL|*Utilisation*<br /> Facultatif, en lecture seule `Integer` propriété<br /><br /> *Description*<br /> Réservé pour un usage ultérieur.<br /><br /> La valeur par défaut de cette propriété est 0.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
|UserName|Cette propriété n'est plus prise en charge.<br /><br /> *Utilisation*<br /> Facultatif, en lecture seule `String` propriété<br /><br /> *Description*<br /> Spécifie une chaîne qui retourne le nom d'utilisateur que l'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] associe à la commande. Pour assurer la compatibilité descendante, cette propriété est ignorée et ne génère pas d'erreur lorsqu'elle est utilisée avec la méthode `Execute` ou `Discover`. Cette propriété est équivalente à la propriété OLE DB DBPROP_USERNAME.<br /><br /> La valeur par défaut de cette propriété est le nom de l'utilisateur qui a ouvert la session ou la connexion active.<br /><br /> Cette propriété peut s'utiliser avec la méthode `Execute`.|  
|VisualMode|*Utilisation*<br /> Facultatif, en écriture seule `Integer` propriété<br /><br /> *Description*<br /> Cette propriété est équivalente à la propriété OLE DB MDPROP_VISUALMODE.<br /><br /> La valeur par défaut de cette propriété est zéro (0), ce qui équivaut à DBPROPVAL_VISUAL_MODE_DEFAULT.<br /><br /> Cette propriété peut s'utiliser avec les méthodes `Discover` et `Execute`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément PropertyList &#40;XMLA&#41;](propertylist-element-xmla.md)  
  
  
