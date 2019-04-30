---
title: Séquence d’échappement appel de procédure | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 914bd4759552680a57c345dc3a7c3bc1bcc103a6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188496"
---
# <a name="procedure-call-escape-sequence"></a>Séquence d’échappement d’appel de procédure
ODBC utilise les séquences d’échappement pour les appels de procédure. La syntaxe de cette séquence d’échappement est comme suit :  
  
 **{**[ ? =]**appeler** *nom de la procédure*[**(**[*paramètre*] [, [*paramètre*]]... **)**]**}**  
  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Échappement ODBC-procédure* :: =  
  
 &#124;*ODBC-ÉCHAP-initiateur* [ ? =] appeler *procédure ODBC ÉCHAP-marque de fin*  
  
 *procedure* ::= *procedure-name* &#124; *procedure-name* (*procedure-parameter-list*)  
  
 *identificateur de la procédure* :: = *nom défini par l’utilisateur*  
  
 *nom de la procédure* :: = *identificateur de la procédure*  
  
 &#124;*-nom du propriétaire*. *identificateur de la procédure*  
  
 &#124; *catalog-name catalog-separator* *procedure-identifier*  
  
 &#124;*nom-catalogue le séparateur de catalogue* [*-nom du propriétaire*]. *identificateur de la procédure*  
  
 (La troisième syntaxe est valide uniquement si la source de données ne prend pas en charge les propriétaires.)  
  
 *nom du propriétaire* :: = *nom défini par l’utilisateur*  
  
 *nom de catalogue* :: = *nom défini par l’utilisateur*  
  
 *séparateur de catalogue* :: = {*défini par l’implémentation*}  
  
 (Le séparateur de catalogue est retourné via **SQLGetInfo** avec l’option d’informations SQL_CATALOG_NAME_SEPARATOR.)  
  
 *liste de paramètres de procédure* :: = *paramètre de procédure*  
  
 &#124; *procedure-parameter*, *procedure-parameter-list*  
  
 *procedure-parameter* ::= *dynamic-parameter* &#124; *literal* &#124; *empty-string*  
  
 *empty-string* ::=  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC ÉCHAP-marque de fin* :: =}  
  
 (Si un paramètre de procédure est une chaîne vide, la procédure utilise la valeur par défaut pour ce paramètre.)  
  
 Pour déterminer si la source de données prend en charge les procédures et le pilote prend en charge la syntaxe d’appel de procédure ODBC, une application peut appeler **SQLGetInfo** avec le type d’information SQL_PROCEDURES.
