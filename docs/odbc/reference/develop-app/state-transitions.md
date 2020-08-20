---
description: Transitions d’état
title: Transitions d’État | Microsoft Docs
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
ms.openlocfilehash: 947be49fc0a77f94c1641bb7c735db3276b49f58
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476361"
---
# <a name="state-transitions"></a>Transitions d’état
ODBC définit des *États* discrets pour chaque environnement, chaque connexion et chaque instruction. Par exemple, l’environnement a trois États possibles : non alloué (dans lequel aucun environnement n’est alloué), alloué (dans lequel un environnement est alloué mais aucune connexion n’est allouée), et connexion (dans laquelle un environnement et une ou plusieurs connexions sont allouées). Les connexions ont sept États possibles ; les instructions ont 13 États possibles.  
  
 Un élément particulier, tel qu’il est identifié par son handle, passe d’un État à un autre lorsque l’application appelle une ou plusieurs fonctions, et passe le handle à cet élément. Ce déplacement est appelé une *transition d’État*. Par exemple, l’allocation d’un descripteur d’environnement avec **SQLAllocHandle** déplace l’environnement de non alloué à alloué, et la libération de ce handle avec **SQLFreeHandle** le retourne de alloué à non alloué. ODBC définit un nombre limité de transitions d’état valides, qui est une autre façon de dire que les fonctions doivent être appelées dans un certain ordre.  
  
 Certaines fonctions, telles que **SQLGetConnectAttr**, n’affectent pas l’état du tout. D’autres fonctions affectent l’état d’un élément unique. Par exemple, **SQLDisconnect** déplace une connexion d’un état de connexion à un État alloué. Enfin, certaines fonctions affectent l’état de plusieurs éléments. Par exemple, l’allocation d’un handle de connexion avec **SQLAllocHandle** déplace une connexion d’un État non alloué à un État alloué et déplace l’environnement d’un État alloué à un état de connexion.  
  
 Si une application appelle une fonction dans le désordre, la fonction retourne une *erreur de transition d’État*. Par exemple, si un environnement est dans un état de connexion et que l’application appelle **SQLFreeHandle** avec ce handle d’environnement, **SQLFREEHANDLE** retourne SQLState HY010 (erreur de séquence de fonction), car il ne peut être appelé que lorsque l’environnement est dans un État alloué. En définissant cette transition d’État comme une transition d’État non valide, ODBC empêche l’application de libérer l’environnement pendant qu’il y a des connexions actives.  
  
 Certaines transitions d’État sont inhérentes à la conception d’ODBC. Par exemple, il n’est pas possible d’allouer un handle de connexion sans allouer au préalable un handle d’environnement, car la fonction qui alloue un handle de connexion requiert un handle d’environnement. D’autres transitions d’État sont appliquées par le gestionnaire de pilotes et les pilotes. Par exemple, **SQLExecute** exécute une instruction préparée. Si le descripteur d’instruction qui lui est passé n’est pas dans un état préparé, **SQLExecute** retourne SQLState HY010 (erreur de séquence de fonction).  
  
 Du point de vue de l’application, les transitions d’État sont généralement simples : les transitions d’état légal tendent à s’adresser à la main avec le déroulement d’une application bien écrite. Les transitions d’État sont plus complexes pour le gestionnaire de pilotes et les pilotes, car elles doivent assurer le suivi de l’état de l’environnement, de chaque connexion et de chaque instruction. La majeure partie de ce travail est effectuée par le gestionnaire de pilotes. la majeure partie du travail qui doit être effectué par les pilotes se produit avec des instructions avec des résultats en attente.  
  
 Les parties 1 et 2 de ce manuel (« introduction à ODBC » et « développement d’applications et de pilotes ») ont tendance à ne pas mentionner explicitement les transitions d’État. Au lieu de cela, ils décrivent l’ordre dans lequel les fonctions doivent être appelées. Par exemple, « exécution d’instructions » indique qu’une instruction doit être préparée avec **SQLPrepare** avant de pouvoir être exécutée avec **SQLExecute**. Pour obtenir une description complète des États et des transitions d’État, notamment quelles transitions sont vérifiées par le gestionnaire de pilotes et qui doivent être vérifiées par les pilotes, consultez [annexe B : tables de transition d’État ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
