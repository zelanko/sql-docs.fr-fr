---
title: Grammaire minimale SQL Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20eee34feadb8e3140f25019ec6b0d036ff02e14
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304990"
---
# <a name="sql-minimum-grammar"></a>Grammaire minimale de SQL
Cette section décrit la syntaxe SQL minimale qu’un conducteur d’ODBC doit supporter. La syntaxe décrite dans cette section est un sous-ensemble de la syntaxe de niveau d’entrée de SQL-92.  
  
 Une application peut utiliser n’importe quelle syntaxe dans cette section et être assuré que tout pilote conforme à l’ODBC prendra en charge cette syntaxe. Pour déterminer si les caractéristiques additionnelles de SQL-92 qui ne figurent pas dans cette section sont prises en charge, l’application doit appeler **SQLGetInfo** avec le type d’information SQL_SQL_CONFORMANCE. Même si le conducteur ne se conforme pas à un niveau de conformité SQL-92, une application peut toujours utiliser la syntaxe décrite dans cette section. Si un conducteur se conforme à un niveau SQL-92, d’autre part, il prend en charge toute la syntaxe incluse dans ce niveau. Cela inclut la syntaxe dans cette section parce que la grammaire minimale décrite ici est un sous-ensemble pur du niveau de conformité SQL-92 le plus bas. Une fois que l’application connaît le niveau SQL-92 pris en charge, elle peut déterminer si une fonctionnalité de niveau supérieur est prise en charge (le cas échéant) en appelant **SQLGetInfo** avec le type d’information individuel correspondant à cette fonctionnalité.  
  
 Les conducteurs qui ne fonctionnent qu’avec des sources de données de lecture seulement pourraient ne pas appuyer les parties de la grammaire incluses dans cette section qui traitent de la modification des données. Une application peut déterminer si une source de données est lue uniquement en appelant **SQLGetInfo** avec le type d’information SQL_DATA_SOURCE_READ_ONLY.  
  
## <a name="statement"></a>.  
 *créer-table-déclaration* ::  
  
 NOM *DE table de base* CREATE TABLE  
  
 (type*de données d’identification de colonnes* [*, type de données d’identification de colonnes*]...)  
  
> [!IMPORTANT]  
>  En tant que *type de données* dans un tableau de *création,* les applications doivent utiliser un type de données à partir de la colonne TYPE_NAME de l’ensemble de résultats retournés par **SQLGetTypeInfo**.  
  
 *supprimer-déclaration-recherché ::*  
  
 DELETE FROM *table-name* [WHERE *search-condition*]  
  
 *drop-table-déclaration* ::MD  
  
 DROP TABLE *base-table-nom*  
  
 *insert-statement* ::MD  
  
 INSERT INTO *nom de table* [(colonne-identifiant [, *colonne-identifiant*]...)] *column-identifier*      VALUES *(insérer-valeur*[, *insérer-valeur*]... )  
  
 *select-statement* ::=  
  
 SELECT [ALL &#124; DISTINCT] *select-list*  
  
 DE *table-référence-liste*  
  
 [Où *la recherche-condition*]  
  
 [*ordonnance par clause*]  
  
 *déclaration* ::- *créer-table-déclaration*  
  
 &#124; *supprimer-déclaration-recherché*  
  
 &#124; *drop-table-statement*  
  
 *&#124;'insert-statement*  
  
 &#124;'énoncé *de sélection*  
  
 &#124; mise *à jour-déclaration-recherchée*  
  
 *mise à jour-déclaration-recherché*  
  
 NOM *de table* UPDATE  
  
 SET *colonne-identificateur* -*expression* &#124; NULL  
  
 [, *colonne-identifiant* *'* expression &#124; NULL]...  
  
 [Où *la recherche-condition*]  
  
 Cette section contient les rubriques suivantes :  
  
-   [Éléments utilisés dans les instructions SQL](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [Support de type de données](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [Types de données de paramètre](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [Marqueurs de paramètres](../../../odbc/reference/appendixes/parameter-markers.md)
