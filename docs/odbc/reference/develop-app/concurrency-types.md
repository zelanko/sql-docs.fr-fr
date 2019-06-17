---
title: Les Types d’accès concurrentiel | Microsoft Docs
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
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 12891d7ee674167157bcb02300d2e4181ef51734
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63012116"
---
# <a name="concurrency-types"></a>Types d’accès concurrentiels
Pour résoudre le problème de concurrence réduite dans les curseurs, ODBC expose quatre types d’accès concurrentiel au curseur :  
  
-   **En lecture seule** le curseur peut lire les données, mais ne peut pas mettre à jour ou supprimer des données. Il s’agit du type de concurrence par défaut. Bien que le SGBD peut verrouiller des lignes pour mettre en œuvre la Repeatable Read et niveaux d’isolement sérialisable, elle peut utiliser des verrous en lecture au lieu de verrous d’écriture. Cela entraîne une simultanéité plus élevée, car au moins peut lire les données.  
  
-   **Verrouillage** le curseur utilise le plus bas niveau de verrouillage nécessaire pour s’assurer qu’il peut mettre à jour ou supprimer des lignes dans le jeu de résultats. Cela se produit généralement dans les niveaux de concurrence très faible, en particulier sur les niveaux d’isolation de transaction Repeatable Read et Serializable.  
  
-   **L’accès concurrentiel optimiste à l’aide de versions de ligne et l’accès concurrentiel optimiste à l’aide de valeurs** le curseur utilise l’accès concurrentiel optimiste : Il met à jour ou supprime des lignes uniquement si elles n’ont pas changé depuis leur dernière lecture. Pour détecter les modifications, il compare les versions de ligne ou de valeurs. Il n’existe aucune garantie que le curseur sera en mesure de mettre à jour ou supprimer une ligne, mais l’accès concurrentiel est beaucoup plus élevée que lorsque le verrouillage est utilisé. Pour plus d’informations, consultez la section suivante, [d’accès concurrentiel optimiste](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Une application spécifie quel type d’accès concurrentiel qu’il veut le curseur à utiliser avec l’attribut d’instruction SQL_ATTR_CONCURRENCY. Pour déterminer quels types sont pris en charge, il appelle **SQLGetInfo** avec l’option SQL_SCROLL_CONCURRENCY.
