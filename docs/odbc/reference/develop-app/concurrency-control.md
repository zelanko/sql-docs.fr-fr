---
description: Contrôle d’accès concurrentiel
title: Contrôle d’accès concurrentiel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e47308cc0224ef73689a3b82d1ab4186fd0c823a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461551"
---
# <a name="concurrency-control"></a>Contrôle d’accès concurrentiel
La *concurrence* est la capacité de deux transactions à utiliser les mêmes données en même temps, et l’isolation des transactions augmente généralement la concurrence. Cela est dû au fait que l’isolation des transactions est généralement implémentée par le verrouillage des lignes, et lorsque davantage de lignes sont verrouillées, moins de transactions peuvent être effectuées sans être bloquées au moins temporairement par une ligne verrouillée. Bien que la concurrence réduite soit généralement acceptée en tant que compromis pour les niveaux d’isolation de transactions les plus élevés nécessaires au maintien de l’intégrité de la base de données, cela peut devenir un problème dans les applications interactives avec une forte activité de lecture/écriture qui utilise des curseurs.  
  
 Supposons, par exemple, qu’une application exécute l’instruction SQL **Select \* from Orders**. Elle appelle **SQLFetchScroll** pour faire défiler le jeu de résultats et permet à l’utilisateur de mettre à jour, supprimer ou insérer des commandes. Une fois que l’utilisateur a mis à jour, supprime ou inséré une commande, l’application valide la transaction.  
  
 Si le niveau d’isolation est lecture renouvelable, la transaction peut dépendre de la façon dont elle est implémentée-verrouiller chaque ligne retournée par **SQLFetchScroll**. Si le niveau d’isolation est sérialisable, la transaction peut verrouiller l’intégralité de la table Orders. Dans les deux cas, la transaction libère ses verrous uniquement lorsqu’elle est validée ou restaurée. Par conséquent, si l’utilisateur passe beaucoup de temps à lire les commandes et à mettre à jour, supprimer ou insérer très peu de temps, la transaction peut facilement verrouiller un grand nombre de lignes, ce qui les rend indisponibles pour les autres utilisateurs.  
  
 Il s’agit d’un problème même si le curseur est en lecture seule et que l’application permet à l’utilisateur de lire uniquement les commandes existantes. Dans ce cas, l’application valide la transaction et libère les verrous lorsqu’elle appelle **SQLCloseCursor** (en mode de validation automatique) ou **SQLEndTran** (en mode de validation manuelle).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types d’accès concurrentiels](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md)
