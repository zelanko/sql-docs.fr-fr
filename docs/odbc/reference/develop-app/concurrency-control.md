---
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
ms.openlocfilehash: 8afba3b3b8c8fee1307473c790186d509b37d982
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294849"
---
# <a name="concurrency-control"></a>Contrôle d’accès concurrentiel
*La concordance* est la capacité de deux transactions d’utiliser les mêmes données en même temps, et avec l’isolement accru des transactions vient généralement la concurrence réduite. C’est parce que l’isolement des transactions est généralement mis en œuvre par des rangées de verrouillage, et comme plus de lignes sont verrouillées, moins de transactions peuvent être effectuées sans être bloqués au moins temporairement par une rangée verrouillée. Bien que la concurrence réduite soit généralement acceptée comme un compromis pour les niveaux plus élevés d’isolement des transactions nécessaires pour maintenir l’intégrité de la base de données, elle peut devenir un problème dans les applications interactives avec une activité de lecture/écriture élevée qui utilisent des curseurs.  
  
 Supposons, par exemple, qu’une application exécute la déclaration SQL **SELECT \* FROM Orders**. Il appelle **SQLFetchScroll** pour faire défiler l’ensemble de résultats et permet à l’utilisateur de mettre à jour, supprimer ou insérer des commandes. Une fois que l’utilisateur met à jour, supprime ou insère une commande, l’application engage la transaction.  
  
 Si le niveau d’isolement est répétable Lire, la transaction pourrait - selon la façon dont elle est mise en œuvre - verrouiller chaque rangée retournée par **SQLFetchScroll**. Si le niveau d’isolement est sérialiser, la transaction peut verrouiller la totalité de la table des commandes. Dans les deux cas, la transaction ne libère ses verrous que lorsqu’elle est commise ou annulée. Donc, si l’utilisateur passe beaucoup de temps à lire les commandes et très peu de temps à mettre à jour, à les supprimer ou à les insérer, la transaction pourrait facilement verrouiller un grand nombre de lignes, les rendant indisponibles pour les autres utilisateurs.  
  
 Il s’agit d’un problème même si le curseur est lu uniquement et l’application permet à l’utilisateur de lire uniquement les commandes existantes. Dans ce cas, l’application commet la transaction et libère des verrous lorsqu’elle appelle **SQLCloseCursor** (en mode auto-commit) ou **SQLEndTran** (en mode engagement manuel).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types d’accès concurrentiels](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md)
