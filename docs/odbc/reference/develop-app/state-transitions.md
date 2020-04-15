---
title: Transitions d’État (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC]
- unallocated state [ODBC]
- handles [ODBC], state transitions
- allocated state [ODBC]
- connection state [ODBC]
ms.assetid: fc741611-6535-43cc-8156-6d897d04664e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a480b7ff8953ef94f0efc4886a09731730a61b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299692"
---
# <a name="state-transitions"></a>Transitions d’état
ODBC définit *les états* discrets pour chaque environnement, chaque connexion et chaque énoncé. Par exemple, l’environnement a trois états possibles : non alloué (dans lequel aucun environnement n’est alloué), alloué (dans lequel un environnement est alloué mais aucune connexion n’est allouée), et Connexion (dans lequel un environnement et une ou plusieurs connexions sont alloués). Les connexions ont sept états possibles; déclarations ont 13 États possibles.  
  
 Un élément particulier, tel qu’identifié par sa poignée, se déplace d’un état à l’autre lorsque l’application appelle une certaine fonction ou fonctions et passe la poignée à cet élément. Un tel mouvement est appelé une *transition d’État*. Par exemple, l’attribution d’une poignée d’environnement avec **SQLAllocHandle** déplace l’environnement de Non-allocaté à alloué, et libérant cette poignée avec **SQLFreeHandle** le renvoie de Allocated à Unallocated. L’ODBC définit un nombre limité de transitions d’État légales, ce qui est une autre façon de dire que les fonctions doivent être appelées dans un certain ordre.  
  
 Certaines fonctions, telles que **SQLGetConnectAttr**, n’affectent pas du tout l’état. D’autres fonctions affectent l’état d’un seul élément. Par exemple, **SQLDisconnect** déplace une connexion d’un état de connexion à un état alloué. Enfin, certaines fonctions affectent l’état de plus d’un élément. Par exemple, l’attribution d’une poignée de connexion avec **SQLAllocHandle** déplace une connexion d’un état non alloué à un état alloué et déplace l’environnement d’un État alloué à un état de connexion.  
  
 Si une application appelle une fonction hors de l’ordre, la fonction renvoie une erreur de *transition d’état*. Par exemple, si un environnement est dans un état de connexion et que l’application appelle **SQLFreeHandle** avec cette poignée d’environnement, **SQLFreeHandle** retourne SQLSTATE HY010 (erreur de séquence de fonction), car il ne peut être appelé que lorsque l’environnement est dans un état alloué. En définissant cela comme une transition d’état invalide, ODBC empêche l’application de libérer l’environnement pendant qu’il y a des connexions actives.  
  
 Certaines transitions d’état sont inhérentes à la conception de l’ODBC. Par exemple, il n’est pas possible d’allouer une poignée de connexion sans d’abord allouer une poignée d’environnement, car la fonction qui alloue une poignée de connexion nécessite une poignée d’environnement. D’autres transitions d’état sont appliquées par le gestionnaire de conducteur et les conducteurs. Par exemple, **SQLExecute** exécute une déclaration préparée. Si la poignée de déclaration qui lui est transmise n’est pas à l’état préparé, **SQLExecute renvoie** SQLSTATE HY010 (erreur de séquence de fonction).  
  
 Du point de vue de l’application, les transitions d’état sont généralement simples : les transitions d’état légal ont tendance à aller de pair avec le flux d’une application bien écrite. Les transitions d’état sont plus complexes pour le gestionnaire de conducteur et les pilotes parce qu’ils doivent suivre l’état de l’environnement, chaque connexion, et chaque déclaration. La plupart de ce travail est effectué par le gestionnaire de chauffeur; la plupart du travail qui doit être effectué par les conducteurs se produit avec des déclarations avec des résultats en attente.  
  
 Les parties 1 et 2 de ce manuel (« Introduction à ODBC » et « Développer des applications et des conducteurs ») ont tendance à ne pas mentionner explicitement les transitions d’état. Au lieu de cela, ils décrivent l’ordre dans lequel les fonctions doivent être appelées. Par exemple, « Déclarations d’exécution » stipule qu’une déclaration doit être préparée avec **SQLPrepare** avant qu’elle puisse être exécutée avec **SQLExecute**. Pour une description complète des états et des transitions de l’État, y compris quelles transitions sont vérifiées par le gestionnaire de conducteur et qui doivent être vérifiées par les conducteurs, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
