---
title: Séquence d’évasion d’appel de procédure (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1194efe6a21c456a722ccd4352661c998f0316d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298219"
---
# <a name="procedure-call-escape-sequence"></a>Séquence d’échappement d’appel de procédure
ODBC utilise des séquences d’évasion pour les appels de procédure. La syntaxe de cette séquence d’évasion est la suivante :  
  
 **Nom**de la procédure**d’appel** *procedure-name***[[?] [[,]...***parameter**parameter* **)**]**}**  
  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC-procédure-évasion* ::  
  
 &#124; *ODBC-esc-initiateur* [?] procédure d’appel *ODBC-esc-terminator*  
  
 *procédure* :: nom *de procédure* &#124; nom *de procédure* *(procédure-paramètre-liste*)  
  
 *procédure-identifiant* ::- *nom défini par l’utilisateur*  
  
 *nom de procédure* ::-procédure-identifiant *procedure-identifier*  
  
 &#124; nom *du propriétaire*. *procédure-identifiant*  
  
 &#124; *catalogue-nom catalogue-séparation* *de la procédure-identifiant*  
  
 &#124; *catalogue-nom catalogue-séparateur* *[nom du propriétaire*]. *procédure-identifiant*  
  
 (La troisième syntaxe n’est valide que si la source de données ne prend pas en charge les propriétaires.)  
  
 *nom du propriétaire* ::md nom *défini par l’utilisateur*  
  
 *nom du catalogue* ::md nom *défini par l’utilisateur*  
  
 *catalogue-séparateur* *::''''''' 'implémenté-défini'*  
  
 (Le séparateur du catalogue est retourné par **SQLGetInfo** avec l’option d’information SQL_CATALOG_NAME_SEPARATOR.)  
  
 *procédure-paramètre-liste* ::md *procédure-paramètre*  
  
 &#124; de *la procédure-paramètre*, *procédure-paramètre-liste*  
  
 *procédure-paramètre* :: *dynamic-parameter* &#124; *littéral* &#124; *empty-string*  
  
 *corde vide* ::MD  
  
 *ODBC-esc-initiateur* ::  
  
 *ODBC-esc-terminator* ::  
  
 (Si un paramètre de procédure est une chaîne vide, la procédure utilise la valeur par défaut pour ce paramètre.)  
  
 Pour déterminer si la source de données prend en charge les procédures et le conducteur prend en charge la syntaxe d’invocation de la procédure ODBC, une application peut appeler **SQLGetInfo** avec le type d’information SQL_PROCEDURES.
