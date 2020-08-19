---
description: Limitations de l’utilisation des curseurs de jeu de clés
title: Limitations de l’utilisation de curseurs de jeu de clés | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 611bc032c51760742e5dce4dfbd8e1fa4fe33d0f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483472"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Limitations de l’utilisation des curseurs de jeu de clés
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Vous devez être en mesure de récupérer une seule colonne ROWID pour la table interrogée. Un curseur piloté par jeu de clés ne peut pas être utilisé sur des jointures, des requêtes ou des instructions qui contiennent des clauses DISTINCT, GROUP BY, UNION, INTERSECT ou MINUS.  
  
 En outre, si votre application utilise des alias de table, les curseurs de jeu de clés ne fonctionneront pas. les types de curseurs avant uniquement ou statiques sont requis. L’utilisation du type de curseur de jeu de clés avec des alias de table provoque l’erreur suivante : « [Microsoft] [ODBC Driver for Oracle] ne peut pas utiliser de curseur de jeu de clés lors de la jointure, avec Union, Intersect ou moins, ou en lecture seule du jeu de résultats. »  
  
> [!NOTE]  
>  En raison de la façon dont le pilote gère l’instruction SQL qui est envoyée au serveur Oracle, Oracle retourne en interne le message d’erreur suivant : « ORA-00964 : le nom de la table ne figure pas dans la liste. »
