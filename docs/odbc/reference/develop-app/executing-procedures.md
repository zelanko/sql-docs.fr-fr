---
title: L’exécution de procédures | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff234d1d8e099611c8718eac5ae3b584e926a2bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061967"
---
# <a name="executing-procedures"></a>Exécution de procédures
ODBC définit une séquence d’échappement standard pour l’exécution de procédures. Pour connaître la syntaxe de cette séquence et un exemple de code qui l’utilise, consultez [les appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Pour exécuter une procédure, une application effectue les actions suivantes :  
  
1.  Définit les valeurs des paramètres. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
2.  Appels **SQLExecDirect** et lui passe une chaîne contenant l’instruction SQL qui exécute la procédure. Cette instruction peut utiliser la séquence d’échappement définie par la syntaxe ODBC ou propres au SGBD ; instructions qui utilisent la syntaxe de SGBD spécifiques ne sont pas interopérables.  
  
3.  Lorsque **SQLExecDirect** est appelée, le pilote :  
  
    -   Récupère les valeurs de paramètre en cours et les convertit en fonction des besoins. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
    -   Appelle la procédure dans la source de données et envoie les valeurs de paramètre converti. Comment le pilote appelle la procédure est spécifique au pilote. Par exemple, il peut modifier l’instruction SQL pour utiliser la grammaire SQL de la source de données et de soumettre cette instruction pour l’exécution, ou elle peut appeler la procédure directement à l’aide d’un mécanisme d’appel de procédure distante (RPC) est défini dans le protocole de flux de données du SGBD.  
  
    -   Retourne les valeurs des paramètres de sortie ou aucune entrée/sortie ou la valeur de retour de procédure, en supposant que la procédure réussit. Ces valeurs ne soient pas disponibles qu’après le traitement de tous les autres résultats (nombre de lignes et des jeux de résultats) générés par la procédure. Si la procédure échoue, le pilote retourne les erreurs.
