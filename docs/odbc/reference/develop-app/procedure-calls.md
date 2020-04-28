---
title: Appels de procédure | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282229"
---
# <a name="procedure-calls"></a>Appels de procédure
Une *procédure* est un objet exécutable stocké dans la source de données. Généralement, il s'agit d'une ou plusieurs instructions SQL qui ont été précompilées. La séquence d’échappement pour appeler une procédure est  
  
 **{**[**? =**]**Call** *procedure-Name*[**(**[*paramètre*] [**,**[*paramètre*]]... **)**]**}**  
  
 où *procédure-Name* spécifie le nom d’une procédure et un *paramètre* spécifie un paramètre de procédure.  
  
 Pour plus d’informations sur la séquence d’échappement d’appel de procédure, consultez [séquence d’échappement d’appel de procédure](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md) dans l’annexe C : grammaire SQL.  
  
 Une procédure peut avoir zéro, un ou plusieurs paramètres. Elle peut également retourner une valeur, comme indiqué par le marqueur de paramètre facultatif **? =** au début de la syntaxe. Si le *paramètre* est une entrée ou un paramètre d’entrée/sortie, il peut s’agir d’un littéral ou d’un marqueur de paramètre. Toutefois, les applications interopérables doivent toujours utiliser des marqueurs de paramètres, car certaines sources de données n’acceptent pas les valeurs de paramètre littérales. Si le *paramètre* est un paramètre de sortie, il doit s’agir d’un marqueur de paramètre. Les marqueurs de paramètres doivent être liés à **SQLBindParameter** avant l’exécution de l’instruction d’appel de procédure.  
  
 Les paramètres d'entrée et d'entrée/sortie peuvent être omis dans les appels de procédure. Si une procédure est appelée avec des parenthèses mais sans aucun paramètre, tel que {Call *procedure-Name*()}, le pilote demande à la source de données d’utiliser la valeur par défaut pour le premier paramètre. Si la procédure n’a pas de paramètres, cela peut provoquer l’échec de la procédure. Si une procédure est appelée sans parenthèses, telle que {Call *procedure-Name*}, le pilote n’envoie aucune valeur de paramètre.  
  
 Des littéraux peuvent être spécifiés comme paramètres d'entrée et d'entrée/sortie dans les appels de procédure. Par exemple, supposons que la procédure **InsertOrder** a cinq paramètres d’entrée. L’appel suivant à **InsertOrder** omet le premier paramètre, fournit un littéral pour le deuxième paramètre et utilise un marqueur de paramètre pour les troisième, quatrième et cinquième paramètres :  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 Notez que si un paramètre est omis, la virgule qui le sépare des autres paramètres doit toujours apparaître. Si un paramètre d'entrée ou d'entrée/sortie est omis, la procédure utilise la valeur par défaut du paramètre. Une autre façon de spécifier la valeur par défaut d’un paramètre d’entrée ou d’entrée/sortie consiste à définir la valeur de la mémoire tampon de longueur/d’indicateur associée au paramètre sur SQL_DEFAULT_PARAM.  
  
 Si un paramètre d’entrée/sortie est omis ou si un littéral est fourni pour le paramètre, le pilote ignore la valeur de sortie. De la même façon, si le marqueur de paramètre pour la valeur de retour d'une procédure est omis, le pilote ignore la valeur de retour. Enfin, si une application spécifie un paramètre de valeur de retour pour une procédure qui ne renvoie pas de valeur, le pilote affecte la valeur SQL_NULL_DATA à la mémoire tampon de l'indicateur/longueur associée au paramètre.  
  
 Supposons que la procédure PARTS_IN_ORDERS crée un jeu de résultats qui contient une liste de commandes qui contiennent un numéro de référence particulier. Le code suivant appelle cette procédure pour le numéro de référence 544 :  
  
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
  
 Pour plus d’informations sur les procédures, consultez [procédures](../../../odbc/reference/develop-app/procedures-odbc.md).
