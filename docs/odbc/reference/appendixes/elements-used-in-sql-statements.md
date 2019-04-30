---
title: Éléments utilisés dans les instructions SQL | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e33beff29463172a26d53953dd5f563fe1f3f5c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240954"
---
# <a name="elements-used-in-sql-statements"></a>Éléments utilisés dans les instructions SQL
Les éléments suivants sont utilisés dans les instructions SQL répertoriées précédemment.  
  
## <a name="element"></a>Élément  
 *identificateur de table de base de* :: = *nom défini par l’utilisateur*  
  
 *nom de table de base de* :: = *identificateur de table de base*  
  
 *valeur booléenne-facteur* :: = [NOT] *principal de la valeur booléenne*  
  
 *boolean-primary* ::= comparison *-predicate* &#124; ( *search-condition* )  
  
 *valeur booléenne-terme* :: = *facteur booléen* [AND *terme de valeur booléenne*]  
  
 *character-string-literal* ::= ''{*character*}...'' (*caractère* est n’importe quel caractère dans le jeu de caractères de la source de données/pilote. Pour inclure un caractère de guillemet littéral (") dans un littéral de chaîne de caractères, utilisez deux caractères de guillemet littéral ['' '].)  
  
 *column-identifier* ::= *user-defined-name*  
  
 *nom de la colonne* :: = [*nom de la table*.] *identificateur de colonne*  
  
 *comparison-operator* ::= < &#124; > &#124; \<= &#124; >= &#124; = &#124; <>  
  
 *prédicat de comparaison* :: = *expression* expression d’opérateur de comparaison  
  
 *type de données* :: = *de type de chaîne de caractères* (*de type de chaîne de caractères* est n’importe quel type de données pour laquelle la colonne « « DATA_TYPE » » dans le jeu de résultats retourné par SQLGetTypeInfo est soit SQL_CHAR ou SQL_VARCHAR.)  
  
 *digit* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9  
  
 *paramètre dynamique* :: = ?  
  
 *expression* :: = terme &#124; expression {+&#124;-} terme  
  
 *factor* ::= [*+*&#124;*-*]*primary*  
  
 *insert-value* ::=  
  
 *dynamic-parameter*  
  
 &#124; *literal*  
  
 &#124; NULL  
  
 &AMP;#124;UTILISATEUR  
  
 *letter* ::= *lower-case-letter &#124; upper-case-letter*  
  
 *literal* ::= *character-string-literal*  
  
 *lettre de scénarios minuscule* :: = un &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; h &#124; je &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y &#124; z  
  
 *clause Order by* :: = ORDER BY *spécification de tri* [, *spécification de tri*]...  
  
 *principal* :: = *nom de colonne*  
  
 &#124; *dynamic-parameter*  
  
 &#124; *literal*  
  
 &#124; ( *expression* )  
  
 *condition de recherche* :: = *terme de valeur booléenne* [ou *condition de recherche*]  
  
 *liste de sélection* :: = \* &#124; *sélectionnez-sous-liste* [, *sélectionnez-sous-liste*]...  (*liste de sélection* ne peut pas contenir de paramètres.)  
  
 *select-sublist* ::= *expression*  
  
 *spécification de tri* :: = {*entier non signé &#124; nom-colonne*} [*ASC &#124; DESC*]  
  
 *identificateur de la table* :: = *nom défini par l’utilisateur*  
  
 *nom de la table* :: = *identificateur de table*  
  
 *référence de table* :: = *-nom de la table*  
  
 *liste de références de table* :: = *référence de table* [,*référence de table*]...  
  
 *term* ::= *factor* &#124; *term* {\*&#124;*/*} *factor*  
  
 *unsigned-integer* ::= {*digit*}  
  
 *lettre de cas supérieur* :: = *A &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; H &#124; je &#124; J &#124; K &#124; L &#124; M &#124; N &#124; O &#124; P &#124;Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; X &#124; Y &#124; Z*  
  
 *nom défini par l’utilisateur* :: = *lettre*[*chiffre* &#124; *lettre* &#124; *_*]...
