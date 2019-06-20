---
title: Grammaire minimale SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26cf76200010edae7f85993ec33eb3722f35e94e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270497"
---
# <a name="sql-minimum-grammar"></a>Grammaire minimale de SQL
Cette section décrit la syntaxe SQL minimale un pilote ODBC doit prendre en charge. La syntaxe décrite dans cette section est un sous-ensemble de la syntaxe de niveau d’entrée de SQL-92.  
  
 Une application peut utiliser une de la syntaxe de cette section et être assurée que n’importe quel pilote compatible ODBC prendra en charge cette syntaxe. Pour déterminer si les fonctionnalités supplémentaires de SQL-92 pas dans cette section sont prises en charge, l’application doit appeler **SQLGetInfo** avec le type d’information SQL_SQL_CONFORMANCE. Même si le pilote n’est pas conforme à n’importe quel niveau de conformité SQL-92, une application peut toujours utiliser la syntaxe décrite dans cette section. Si un pilote est conforme à un niveau de SQL-92, quant à eux, il prend en charge toute la syntaxe incluse dans ce niveau. Cela inclut la syntaxe de cette section, car la grammaire minimale décrite ici est un sous-ensemble pur du plus bas niveau de conformité SQL-92. Une fois que l’application connaît le niveau de SQL-92 pris en charge, il peut déterminer si une fonctionnalité de niveau supérieur est pris en charge (le cas échéant) en appelant **SQLGetInfo** avec le type des informations correspondant à cette fonctionnalité.  
  
 Les pilotes qui fonctionnent uniquement avec les sources de données en lecture seule ne peuvent pas en charge les parties de la grammaire inclus dans cette section qui traitent de la modification des données. Une application peut déterminer si une source de données est en lecture seule en appelant **SQLGetInfo** avec le type d’information SQL_DATA_SOURCE_READ_ONLY.  
  
## <a name="statement"></a>.  
 *create-table-statement* ::=  
  
 CREATE TABLE *nom de table de base*  
  
 (*-identificateur de la colonne le type de données* [*, type de données identificateur de colonne*]...)  
  
> [!IMPORTANT]  
>  Comme un *type de données* dans un *-table-instruction create*, les applications doivent utiliser un type de données à partir de la colonne TYPE_NAME du jeu de résultats retourné par **SQLGetTypeInfo**.  
  
 *delete-statement-searched* ::=  
  
 DELETE FROM *nom de la table* [où *condition de recherche*]  
  
 *drop-table-statement* ::=  
  
 DROP TABLE *nom de table de base*  
  
 *insert-statement* ::=  
  
 INSERT INTO *nom de la table* [( *identificateur de colonne* [, *identificateur de colonne*]...)]      VALEURS (*-valeur à insérer*[, *-valeur à insérer*]...)  
  
 *select-statement* ::=  
  
 SELECT [ALL &#124; DISTINCT] *select-list*  
  
 À partir de *liste de références de table*  
  
 [Où *condition de recherche*]  
  
 [*order-by-clause*]  
  
 *instruction* :: = *-table-instruction create*  
  
 &#124; *delete-statement-searched*  
  
 &#124; *drop-table-statement*  
  
 &#124; *insert-statement*  
  
 &#124; *select-statement*  
  
 &#124; *update-statement-searched*  
  
 *update-statement-searched*  
  
 Mise à jour *-nom de la table*  
  
 Définissez *identificateur de colonne* = {*expression* &#124; NULL}  
  
 [, *column-identifier* = {*expression* &#124; NULL}]...  
  
 [Où *condition de recherche*]  
  
 Cette section contient les rubriques suivantes.  
  
-   [Éléments utilisés dans les instructions SQL](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [Prise en charge des types de données](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [Types de données de paramètre](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [Marqueurs de paramètres](../../../odbc/reference/appendixes/parameter-markers.md)
