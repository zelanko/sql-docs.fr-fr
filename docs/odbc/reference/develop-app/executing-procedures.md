---
title: Procédures d’exécution (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a796c615d7dfdec11a9acb90ab4b5129cf69717
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305710"
---
# <a name="executing-procedures"></a>Exécution de procédures
ODBC définit une séquence d’évacuation standard pour l’exécution des procédures. Pour la syntaxe de cette séquence et un exemple de code qui l’utilise, voir [Procedure Calls](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Pour exécuter une procédure, une application effectue les actions suivantes :  
  
1.  Définit les valeurs de tous les paramètres. Pour plus d’informations, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus tard dans cette section.  
  
2.  Appelle **SQLExecDirect** et lui passe une chaîne contenant la déclaration SQL qui exécute la procédure. Cette déclaration peut utiliser la séquence d’évacuation définie par la syntaxe spécifique à l’ODBC ou au DBMS; les déclarations qui utilisent la syntaxe spécifique à DBMS ne sont pas interopérables.  
  
3.  Lorsque **SQLExecDirect** est appelé, le conducteur:  
  
    -   Récupère les valeurs de paramètres actuelles et les convertit au besoin. Pour plus d’informations, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus tard dans cette section.  
  
    -   Appelle la procédure dans la source de données et lui envoie les valeurs de paramètres converties. La façon dont le conducteur appelle la procédure est spécifique au conducteur. Par exemple, il peut modifier l’énoncé SQL pour utiliser la grammaire SQL de la source de données et soumettre cette déclaration pour exécution, ou il peut appeler la procédure directement à l’aide d’un mécanisme d’appel de procédure à distance (RPC) qui est défini dans le protocole de flux de données du DBMS.  
  
    -   Retourne les valeurs de tout paramètres d’entrée/sortie ou de sortie ou de la valeur de retour de la procédure, en supposant que la procédure réussisse. Ces valeurs pourraient ne pas être disponibles avant que tous les autres résultats (nombres de lignes et ensembles de résultats) générés par la procédure aient été traités. En cas d’échec de la procédure, le conducteur renvoie toute erreur.
