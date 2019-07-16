---
title: Types de curseurs (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], types
ms.assetid: 7cc01544-e814-403b-bbfe-a2750bf921bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 00c89272d121898b6ac5af75022344acf1dceb28
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923857"
---
# <a name="types-of-cursors-ado"></a>Types de curseurs (ADO)
En règle générale, votre application doit utiliser le curseur de la plus simple qui fournit l’accès aux données requises. Toutes les caractéristiques supplémentaires au-delà de ses fonctions de base (avant uniquement, en lecture seule, statique, défilement, sans tampon) a un prix - dans la mémoire du client, de la charge réseau ou les performances. Dans de nombreux cas, les options de curseur par défaut génèrent un curseur plus complexe que votre application a réellement besoin.  
  
 Votre choix du type de curseur dépend de comment votre application utilise le jeu de résultats et également de plusieurs considérations de conception, y compris la taille du jeu de résultats, le pourcentage des données susceptibles d’être utilisés, la sensibilité aux modifications de données et les performances de l’application configuration requise.  
  
 Au minimum, votre choix de curseur dépend de si vous devez modifier ou simplement afficher les données :  
  
-   Si vous souhaitez simplement parcourir un jeu de résultats, mais pas les données modifiées, utilisez un [avant uniquement](../../../ado/guide/data/forward-only-cursors.md) ou [statique](../../../ado/guide/data/static-cursors.md) curseur.  
  
-   Si vous avez un grand jeu de résultats et la nécessité pour sélectionner uniquement quelques lignes, utilisez un [keyset](../../../ado/guide/data/keyset-cursors.md) curseur.  
  
-   Si vous souhaitez synchroniser un jeu de résultats avec récente ajoute, modifie et supprime tous les utilisateurs simultanés, utilisez un [dynamique](../../../ado/guide/data/dynamic-cursors.md) curseur.  
  
 Bien que chaque type de curseur semble différent, n’oubliez pas que ces types de curseur ne sont pas différences majeures en tant que simplement le résultat de caractéristiques et les options qui se chevauchent.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)  
  
-   [Curseurs statiques](../../../ado/guide/data/static-cursors.md)  
  
-   [Curseurs de jeu de clés](../../../ado/guide/data/keyset-cursors.md)  
  
-   [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)   
 [Curseurs statiques](../../../ado/guide/data/static-cursors.md)   
 [Curseurs keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)
