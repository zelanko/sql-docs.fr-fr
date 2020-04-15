---
title: Limitations de l’utilisation des curseurs à clé (fr) Microsoft Docs
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
ms.openlocfilehash: 2aeb5a0c50192118dfff8ed7d866c3911c2b4007
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284149"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Limitations de l’utilisation des curseurs de jeu de clés
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Vous devez être en mesure de récupérer une seule colonne ROWID pour la table interrogée. Un curseur à clé ne peut pas être utilisé sur les jointures, les requêtes ou les déclarations qui contiennent des clauses DISTINCT, GROUP BY, UNION, INTERSECT ou MINUS.  
  
 De plus, si votre application utilise des alias de table, les curseurs à clé ne fonctionneront pas; les types de curseur avant-seulement ou statiques sont exigés. L’utilisation du type curseur de jeu-clé avec des alias de table causera l’erreur suivante : « [Microsoft][pilote ODBC pour Oracle]Ne peut pas utiliser le curseur piloté par Keyset sur l’adhére, avec l’union, le croisement ou moins ou sur l’ensemble de résultats seulement lu. »  
  
> [!NOTE]  
>  En raison de la façon dont le pilote gère la déclaration SQL qui est envoyé au serveur Oracle, Oracle renvoie en interne le message d’erreur suivant: "ORA-00964: nom de table pas dans la liste FROM."
