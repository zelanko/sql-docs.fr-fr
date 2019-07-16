---
title: Les curseurs avant uniquement | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], forward-only
- forward-only cursors [ADO]
ms.assetid: 2b1e062f-3294-4a6f-8241-a17045c4df18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e84fbf2b8fda2fa2b14088af1e0830d8109aba8a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925305"
---
# <a name="forward-only-cursors"></a>Curseurs avant uniquement
Le type de curseur par défaut, appelé un curseur avant uniquement (ou non déroulante), peut avancer uniquement dans le jeu de résultats. Un curseur avant uniquement ne prend pas en charge le défilement (la possibilité de déplacer vers l’avant et vers l’arrière dans le jeu de résultats) ; Il prend uniquement en charge l’extraction de lignes à partir du début à la fin du jeu de résultats. Avec certains curseurs avant uniquement (comme avec la bibliothèque de curseurs SQL Server), toutes les instructions delete, insert et mise à jour effectuées par l’utilisateur actuel (ou validées par d’autres utilisateurs) qu’incidence sur les lignes du jeu de résultats sont visibles que les lignes sont extraites. Cependant, étant donné que le curseur ne permet pas le défilement arrière, les modifications apportées aux lignes de la base de données après l’extraction d’une ligne ne sont pas visibles par le biais du curseur.  
  
 Une fois les données de la ligne actuelle sont traitées, le curseur avant uniquement libère les ressources qui ont été utilisées pour stocker ces données. Les curseurs avant uniquement sont dynamiques par défaut, ce qui signifie que toutes les modifications sont détectées lors du traitement de la ligne active. Cela accélère l’ouverture du curseur et permet au jeu de résultats d’afficher les mises à jour apportées aux tables sous-jacentes.  
  
 Bien que les curseurs avant uniquement ne prennent pas en charge le défilement vers l’arrière, votre application peut retourner au début du jeu de résultats par la fermeture et réouverture du curseur. Il s’agit d’un moyen efficace pour travailler avec petites quantités de données. Comme alternative, votre application peut lire le jeu de résultats une fois, mettre en cache les données localement, puis recherchez le cache de données local.  
  
 Si votre application ne nécessite pas de faire défiler le jeu de résultats, le curseur avant uniquement est la meilleure façon de récupérer des données rapidement avec le moins de surcharge. Utiliser le **adOpenForwardOnly CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur avant uniquement dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs statiques](../../../ado/guide/data/static-cursors.md)   
 [Curseurs keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)
