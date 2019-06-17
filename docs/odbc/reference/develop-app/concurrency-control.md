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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e54298e9c25777f10b92f322f1b1e6a3d94c243
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63191762"
---
# <a name="concurrency-control"></a>Contrôle d'accès concurrentiel
*Accès concurrentiel* est la possibilité de deux transactions utilisent les mêmes données en même temps, et avec accrue des transactions isolation est généralement une concurrence réduite. Il s’agit, car l’isolation des transactions est généralement implémentée par verrouillage de lignes et car plus de lignes sont verrouillés, moins de transactions peuvent être effectuées au moins temporairement bloqué par une ligne verrouillée. Pendant une concurrence réduite est généralement considérée comme un compromis pour les plus élevées niveaux d’isolement nécessaires pour maintenir l’intégrité de base de données, il peut devenir un problème dans les applications interactives avec une activité élevée en lecture/écriture qui utilisent des curseurs.  
  
 Par exemple, une application exécute l’instruction SQL **sélectionnez \* à partir de commandes**. Il appelle **SQLFetchScroll** pour faire défiler le résultat défini et autorise l’utilisateur à mettre à jour, supprimer ou insérer des commandes. Une fois que l’utilisateur met à jour, supprime ou insère une commande, l’application valide la transaction.  
  
 Si le niveau d’isolement est Repeatable Read, la transaction - selon la façon dont il a été implémentée - bloquer chaque ligne retournée par **SQLFetchScroll**. Si le niveau d’isolement est Serializable, la transaction peut verrouiller la table Orders entière. Dans les deux cas, la transaction libère ses verrous uniquement lorsqu’elle est validée ou restaurée. Par conséquent, si l’utilisateur passe beaucoup de temps à lire les commandes et très peu de temps la mise à jour, suppression, ou en les insérant, la transaction n’a pu facilement verrouiller un grand nombre de lignes, ce qui les rend indisponibles à d’autres utilisateurs.  
  
 Il s’agit d’un problème même si le curseur est en lecture seule et l’application permet à l’utilisateur à lire uniquement les commandes existantes. Dans ce cas, l’application valide la transaction et libère les verrous, lorsqu’il appelle **SQLCloseCursor** (en mode de validation automatique) ou **SQLEndTran** (en mode de validation manuelle).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types d’accès concurrentiels](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md)
