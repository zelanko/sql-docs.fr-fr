---
title: Appels de procédure (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure calls
- procedure calls [ODBC]
ms.assetid: 145130cc-40e7-4722-8417-dff131084752
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9c52e72512c8b81c6872461207f235ea2731ac5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282229"
---
# <a name="procedure-calls"></a>Appels de procédure
Une *procédure* est un objet exécutable stocké sur la source de données. Généralement, il s'agit d'une ou plusieurs instructions SQL qui ont été précompilées. La séquence d’évasion pour appeler une procédure est  
  
 **[?]****call** *procedure-name*[**[**[*[paramètre*]**,***[paramètre]...***?=** **)**]**}**  
  
 lorsque le *nom de la procédure* spécifie le nom d’une procédure et le *paramètre* spécifie un paramètre de procédure.  
  
 Pour plus d’informations sur la séquence d’évasion d’appel [d’appel de procédure,](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md) voir Procédure Call Escape Sequence à l’annexe C: SQL Grammar.  
  
 Une procédure peut avoir zéro, un ou plusieurs paramètres. Il peut également retourner une valeur, comme indiqué par le marqueur de paramètre optionnel **? '** au début de la syntaxe. Si *le paramètre* est une entrée ou un paramètre d’entrée/sortie, il peut s’agir d’un marqueur littéral ou d’un marqueur de paramètres. Cependant, les applications interopérables doivent toujours utiliser des marqueurs de paramètres parce que certaines sources de données n’acceptent pas les valeurs de paramètres littéral. Si *le paramètre* est un paramètre de sortie, il doit s’agir d’un marqueur de paramètres. Les marqueurs de paramètres doivent être reliés à **SQLBindParameter** avant l’exécution de la déclaration d’appel de la procédure.  
  
 Les paramètres d'entrée et d'entrée/sortie peuvent être omis dans les appels de procédure. Si une procédure est appelée avec des parenthèses mais sans aucun paramètre, tel que le *nom de procédure*d’appel , le conducteur demande à la source de données d’utiliser la valeur par défaut pour le premier paramètre. Si la procédure n’a pas de paramètres, cela pourrait entraîner l’échec de la procédure. Si une procédure est appelée sans parenthèses, comme le *nom de la procédure*d’appel, le conducteur n’envoie aucune valeur de paramètre.  
  
 Des littéraux peuvent être spécifiés comme paramètres d'entrée et d'entrée/sortie dans les appels de procédure. Supposons, par exemple, que la procédure **InsertOrder** comporte cinq paramètres d’entrée. L’appel suivant à **InsertOrder** omet le premier paramètre, fournit un paramètre littéral pour le deuxième, et utilise un marqueur de paramètres pour les troisième, quatrième et cinquième paramètres:  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 Notez que si un paramètre est omis, la virgule qui le délimite d’autres paramètres doit encore apparaître. Si un paramètre d'entrée ou d'entrée/sortie est omis, la procédure utilise la valeur par défaut du paramètre. Une autre façon de spécifier la valeur par défaut d’un paramètre d’entrée ou d’entrée/sortie consiste à définir la valeur du tampon longueur/indicateur lié au paramètre à SQL_DEFAULT_PARAM.  
  
 Si un paramètre d’entrée/sortie est omis ou si un littéraux est fourni pour le paramètre, le conducteur écarte la valeur de sortie. De la même façon, si le marqueur de paramètre pour la valeur de retour d'une procédure est omis, le pilote ignore la valeur de retour. Enfin, si une application spécifie un paramètre de valeur de retour pour une procédure qui ne renvoie pas de valeur, le pilote affecte la valeur SQL_NULL_DATA à la mémoire tampon de l'indicateur/longueur associée au paramètre.  
  
 Supposons que la procédure PARTS_IN_ORDERS crée un ensemble de résultats qui contient une liste d’ordres qui contiennent un numéro de pièce particulier. Le code suivant appelle cette procédure pour le numéro de pièce 544:  
  
```  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_SLONG, SQL_INTEGER, 0, 0,  
                  &PartID, 0, PartIDInd);  
  
// Place the department number in PartID.  
PartID = 544;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "{call PARTS_IN_ORDERS(?)}", SQL_NTS);  
```  
  
 Pour déterminer si une source de données prend en charge les procédures, une application appelle **SQLGetInfo** avec l’option SQL_PROCEDURES.  
  
 Pour plus d’informations sur les procédures, voir [Procédures](../../../odbc/reference/develop-app/procedures-odbc.md).
