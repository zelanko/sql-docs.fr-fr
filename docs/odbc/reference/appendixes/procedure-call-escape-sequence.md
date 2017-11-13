---
title: "Séquence d’échappement de procédure appel | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0ba89ae47d223ea17f02cb07976510d78ff3660e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="procedure-call-escape-sequence"></a>Séquence d’échappement d’appel de procédure
ODBC utilise les séquences d’échappement pour les appels de procédure. La syntaxe de cette séquence d’échappement est comme suit :  
  
 **{**[ ? =]**appeler** *-nom de la procédure*[**(**[*paramètre*] [, [*paramètre*]]... **)**]**}**  
  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Échappement de procédure de ODBC* :: =  
  
 &#124; *ODBC ÉCHAP-initiateur* [ ? =] appeler *procédure ODBC ÉCHAP-marque de fin*  
  
 *procédure* :: = *-nom de la procédure* &#124; *-nom de la procédure* (*liste de paramètres de procédure*)  
  
 *identificateur de la procédure* :: = *nom défini par l’utilisateur*  
  
 *nom de la procédure* :: = *identificateur de la procédure*  
  
 &#124; *-nom du propriétaire*. *identificateur de la procédure*  
  
 &#124; *nom-catalogue le séparateur de catalogue* *identificateur de la procédure*  
  
 &#124; *nom-catalogue le séparateur de catalogue* [*-nom du propriétaire*]. *identificateur de la procédure*  
  
 (La syntaxe de la troisième est valide uniquement si la source de données ne prend pas en charge les propriétaires).  
  
 *nom du propriétaire* :: = *nom défini par l’utilisateur*  
  
 *nom de catalogue* :: = *nom défini par l’utilisateur*  
  
 *séparateur de catalogue* :: = {*défini par l’implémentation*}  
  
 (Le séparateur de catalogue est retourné via **SQLGetInfo** avec l’option d’informations SQL_CATALOG_NAME_SEPARATOR.)  
  
 *liste des paramètres de procédure* :: = *paramètre de procédure*  
  
 &#124; *paramètre de procédure*, *liste de paramètres de procédure*  
  
 *paramètre de procédure* :: = *-paramètre dynamique* &#124; *littéral* &#124; *une chaîne vide*  
  
 *une chaîne vide* :: =  
  
 *ÉCHAP ODBC-initiateur* :: = {}  
  
 *Terminateur d’ÉCHAP ODBC* :: =}  
  
 (Si un paramètre de procédure est une chaîne vide, la procédure utilise la valeur par défaut pour ce paramètre.)  
  
 Pour déterminer si la source de données prend en charge les procédures et le pilote prend en charge la syntaxe d’appel de procédure ODBC, une application peut appeler **SQLGetInfo** avec le type d’informations SQL_PROCEDURES.

