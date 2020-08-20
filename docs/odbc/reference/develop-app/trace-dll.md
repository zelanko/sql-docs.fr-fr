---
description: DLL de traçage
title: DLL de trace | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace DLLs [ODBC]
- tracing options [ODBC], trace DLLs
ms.assetid: 5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1791b72b5f7e836fba05275f87bd57948a273775
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487502"
---
# <a name="trace-dll"></a>DLL de traçage
La DLL qui effectue le suivi est l’un des composants ODBC Core. La DLL de suivi est actuellement fournie en tant qu’exemple de DLL dans le composant ODBC du SDK Windows et a été précédemment incluse dans le kit de développement logiciel (SDK) Microsoft Data Access Components (MDAC). Par conséquent, l’entrée de Registre, l’interface et l’exemple de code de la DLL de trace sont disponibles. Cette DLL peut être remplacée par une DLL de trace générée par un utilisateur ODBC ou un fournisseur tiers. Un nom différent de la DLL de trace d’origine doit être attribué à une DLL de trace personnalisée. Les dll de trace doivent être installées dans le répertoire système ou ne pas se charger. Les chaînes de connexion ne sont pas transmises à la DLL de trace par le gestionnaire de pilotes.  
  
 La DLL de suivi trace les arguments d’entrée, les arguments de sortie, les arguments différés, les codes de retour et les SQLSTATEs. Lorsque le suivi est activé, le gestionnaire de pilotes appelle la DLL de trace à deux points : une fois lors de l’entrée de la fonction (avant la validation de l’argument) et de nouveau juste avant le retour de la fonction.  
  
 Quand une application appelle une fonction, le gestionnaire de pilotes appelle une fonction de trace dans la DLL de trace avant d’appeler la fonction dans le pilote ou de traiter l’appel lui-même. Chaque fonction ODBC a une fonction trace correspondante (avec le préfixe *trace*) qui est identique à la fonction ODBC, à l’exception du nom. Lorsque la fonction trace est appelée, la DLL de trace capture les arguments d’entrée et retourne un code de retour. Étant donné que la DLL de trace est appelée avant que le gestionnaire de pilotes valide les arguments, les appels de fonction non valides sont suivis, de sorte que les erreurs de transition d’État et les arguments non valides sont journalisés.  
  
 Après l’appel de la fonction trace dans la DLL de trace, le gestionnaire de pilotes appelle la fonction ODBC dans le pilote. Il appelle ensuite **TraceReturn** dans la dll de trace. Cette fonction accepte deux arguments : la valeur retournée par la DLL de trace pour la fonction trace et le code de retour renvoyé par le pilote au gestionnaire de pilotes pour la fonction ODBC (ou la valeur retournée par le gestionnaire de pilotes lui-même si elle a traité la fonction). La fonction utilise la valeur retournée pour la fonction trace pour manipuler les valeurs d’argument d’entrée capturées. Elle écrit le code retourné pour la fonction ODBC dans le fichier journal (ou l’affiche de manière dynamique, si elle est activée). Il déréférence les pointeurs d’argument de sortie et journalise les valeurs d’argument de sortie.
