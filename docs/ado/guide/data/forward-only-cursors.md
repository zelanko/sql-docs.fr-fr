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
manager: craigg
ms.openlocfilehash: ee3d8a80598e3f41bd6bfaf9a493639ee36cd3ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802837"
---
# <a name="forward-only-cursors"></a>Curseurs avant uniquement
Le type de curseur par défaut, appelé un curseur avant uniquement (ou non déroulante), peut avancer uniquement dans le jeu de résultats. Un curseur avant uniquement ne prend pas en charge le défilement (la possibilité de déplacer vers l’avant et vers l’arrière dans le jeu de résultats) ; Il prend uniquement en charge l’extraction de lignes à partir du début à la fin du jeu de résultats. Avec certains curseurs avant uniquement (comme avec la bibliothèque de curseurs SQL Server), toutes les instructions delete, insert et mise à jour effectuées par l’utilisateur actuel (ou validées par d’autres utilisateurs) qu’incidence sur les lignes du jeu de résultats sont visibles que les lignes sont extraites. Étant donné que le curseur ne peut pas être l’objet d’un défilement vers l’arrière, toutefois, les modifications apportées aux lignes de la base de données une fois que la ligne a été extraite ne sont pas visibles via le curseur.  
  
 Une fois les données de la ligne actuelle sont traitées, le curseur avant uniquement libère les ressources qui ont été utilisées pour stocker ces données. Les curseurs avant uniquement sont dynamiques par défaut, ce qui signifie que toutes les modifications sont détectées lors du traitement de la ligne actuelle. Cela permet l’ouverture de curseur plus rapide et le jeu de résultats à afficher les mises à jour apportées aux tables sous-jacentes.  
  
 Bien que les curseurs avant uniquement ne prennent pas en charge le défilement vers l’arrière, votre application peut retourner au début du jeu de résultats par la fermeture et réouverture du curseur. Il s’agit d’un moyen efficace pour travailler avec petites quantités de données. Comme alternative, votre application peut lire le jeu de résultats une fois, mettre en cache les données localement, puis recherchez le cache de données local.  
  
 Si votre application ne nécessite pas de faire défiler le jeu de résultats, le curseur avant uniquement est la meilleure façon de récupérer des données rapidement avec le moins de surcharge. Utiliser le **adOpenForwardOnly CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur avant uniquement dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs statiques](../../../ado/guide/data/static-cursors.md)   
 [Curseurs keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)
