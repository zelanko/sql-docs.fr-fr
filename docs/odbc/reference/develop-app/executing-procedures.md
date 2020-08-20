---
description: Exécution de procédures
title: Exécution des procédures | Microsoft Docs
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
ms.openlocfilehash: e4a5f790a0e79e313924e9408f9338483931691c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499910"
---
# <a name="executing-procedures"></a>Exécution de procédures
ODBC définit une séquence d’échappement standard pour l’exécution des procédures. Pour obtenir la syntaxe de cette séquence et un exemple de code qui l’utilise, consultez [appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Pour exécuter une procédure, une application effectue les actions suivantes :  
  
1.  Définit les valeurs de tous les paramètres. Pour plus d’informations, consultez [paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
2.  Appelle **SQLExecDirect** et lui transmet une chaîne contenant l’instruction SQL qui exécute la procédure. Cette instruction peut utiliser la séquence d’échappement définie par ODBC ou la syntaxe spécifique au SGBD. les instructions qui utilisent la syntaxe propre au SGBD ne sont pas interopérables.  
  
3.  Lorsque **SQLExecDirect** est appelé, le pilote :  
  
    -   Récupère les valeurs de paramètres actuelles et les convertit si nécessaire. Pour plus d’informations, consultez [paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.  
  
    -   Appelle la procédure dans la source de données et l’envoie aux valeurs de paramètre converties. La façon dont le pilote appelle la procédure est spécifique au pilote. Par exemple, il peut modifier l’instruction SQL pour utiliser la grammaire SQL de la source de données et envoyer cette instruction pour exécution, ou elle peut appeler la procédure directement à l’aide d’un mécanisme d’appel de procédure distante (RPC) défini dans le protocole de flux de données du SGBD.  
  
    -   Retourne les valeurs de tous les paramètres d’entrée/sortie ou de sortie ou la valeur de retour de la procédure, en supposant que la procédure aboutisse. Ces valeurs peuvent ne pas être disponibles tant que tous les autres résultats (nombres de lignes et jeux de résultats) générés par la procédure n’ont pas été traités. Si la procédure échoue, le pilote retourne les erreurs éventuelles.
