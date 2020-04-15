---
title: Éléments utilisés dans les déclarations SQL Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], elements supported
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49a1cd54957426d4d14d84d43df670c8c3d96189
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307020"
---
# <a name="elements-used-in-sql-statements"></a>Éléments utilisés dans les instructions SQL
Les éléments suivants sont utilisés dans les relevés SQL énumérés précédemment.  
  
## <a name="element"></a>Élément  
 *base-table-identifiant* *:'nom défini par l’utilisateur*  
  
 *base-table-nom* *::'base-table-identifiant*  
  
 *facteur boolean* ::'[PAS] *boolean-primaire*  
  
 *boolean-primaire* ::- comparaison *-predicate* &#124; ( *search-condition* )  
  
 *boolean-term* ::md *boolean-factor* [ET *boolean-term*]  
  
 *caractère-corde-littérale* ::''''''''''''''''''''''''''''''''''''''''''''''*character* (*le caractère* est n’importe quel personnage dans l’ensemble de caractères de la source de pilote/de données. Pour inclure un seul personnage de citation littérale ('') dans un caractère-corde-littérale, utilisez deux caractères de citation littérale [''''].)  
  
 *colonne-identificateur* *::-nom défini par l’utilisateur*  
  
 *nom de colonne* ::*[nom de table*.] *colonne-identificateur*  
  
 *comparaison-opérateur* ::md < &#124; > &#124; \<' &#124; >' &#124; ' &#124; <>  
  
 *comparaison-prédicate* ::expression *d’expression* comparaison-opérateur expression  
  
 *type de données* :: type *caractère-chaîne* *(type de chaîne de caractères* est n’importe quel type de données pour lequel la colonne "DATA_TYPE" dans l’ensemble de résultat retourné par SQLGetTypeInfo est soit SQL_CHAR ou SQL_VARCHAR.)  
  
 *chiffre* :: 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9  
  
 *dynamique-paramètre* ::md ?  
  
 *expression* :: terme &#124; expression ' terme&#124;  
  
 *facteur* ::*+* [&#124;*-*]*primaire*  
  
 *valeur d’insertion* ::MD  
  
 *paramètre dynamique*  
  
 &#124; *littéral*  
  
 &#124; NULL  
  
 &#124;'UTILISATEUR  
  
 *lettre* :: - *lettre inférieure-cas &#124;-cas-lettre supérieure*  
  
 *littérale* *::-caractère-corde-littérale*  
  
 *lettre inférieure ::* un &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; h &#124; i &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y &#124; z  
  
 *ordonnance par clause* ::'ORDER BY *tri-spécification* [, *tri-spécification*]...  
  
 *primaire* ::- *nom de colonne*  
  
 &#124; un *paramètre dynamique*  
  
 &#124; *littéral*  
  
 &#124; ( *expression* )  
  
 *recherche-condition* *::boolean-terme* [OU *search-condition*]  
  
 *select-list* ::md \* &#124; *select-sublist* [, *select-sublist*]...  (liste*de sélection* ne peut pas contenir de paramètres.)  
  
 *select-sublist* *::expression*  
  
 *tri-spécification* ::md-*&#124; nom de colonne*non signée - [*ASC &#124; DESC*]  
  
 *tableau-identifiant* ::-nom *défini par l’utilisateur*  
  
 *nom de table* ::' *table-identifiant*  
  
 *référence de table* ::md nom *de table*  
  
 *table-référence-liste* ::md *table-référence* [,*table-référence*]...  
  
 *terme* :: ' *facteur* &#124;\* *terme* '&#124;*/*' *facteur*  
  
 *non signé-integer* *::''' chiffre*'  
  
 *haut-cas-lettre* :: *A &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; H &#124; I &#124; J &#124; K &#124; L &#124; L M &#124; N &#124; O &#124; P &#124; Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; X &#124; Y &#124; Z Z*  
  
 *nom défini par l’utilisateur* : : *lettre**[lettre de &#124; chiffre* *&#124;* *']...*
