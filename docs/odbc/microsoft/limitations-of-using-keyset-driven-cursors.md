---
title: Limitations de l’utilisation de curseurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c4910ebd2c6dd988e937f1e9d6a3281bb0e9741
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192323"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Limitations de l’utilisation des curseurs de jeu de clés
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Vous devez être en mesure de récupérer une seule colonne ROWID pour la table interrogée. Un curseur keyset ne peut pas être utilisé sur les jointures, les requêtes ou les instructions qui contiennent DISTINCT, GROUP BY, UNION, INTERSECT ou moins clauses.  
  
 En outre, si votre application utilise des alias de table, curseurs ne fonctionnent pas ; types de curseurs avant uniquement, ou statiques sont nécessaires. Le jeu de clés à l’aide de type de curseur avec des alias de table entraîne l’erreur suivante : « [Microsoft] [pilote ODBC pour Oracle] ne peut pas utiliser le curseur sur la jointure, avec union, intersect ou moins ou sur lecture seule de jeu de résultats. »  
  
> [!NOTE]  
>  En raison du mode que le pilote gère l’instruction SQL qui est envoyée au serveur Oracle, Oracle retourne en interne le message d’erreur suivant : « ORA-00964 : table nom pas dans à partir de la liste. »
