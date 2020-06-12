---
title: Perspectives dans les modèles multidimensionnels | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- hiding objects from perspective
- renaming perspectives
- attributes [Analysis Services], default members
- removing perspectives
- perspectives [Analysis Services]
- names [Analysis Services], perspectives
- cubes [Analysis Services], perspectives
- deleting perspectives
ms.assetid: 5a3d6577-6833-4c24-820c-b65bb856157b
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1c645486a0d328a1074f1a25b730bfbac1b14af
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545835"
---
# <a name="perspectives-in-multidimensional-models"></a>Perspectives dans les modèles multidimensionnels
  Une perspective est un sous-ensemble de cube créé pour une application ou un groupe d'utilisateurs particuliers. Le cube lui-même est la perspective par défaut. Une perspective se présente à un client sous forme de cube. Lorsqu'un utilisateur affiche une perspective, elle ressemble à n'importe quel autre cube. Toute modification apportée aux données du cube via l'écriture différée dans la perspective affecte le cube d'origine. Pour plus d’informations sur les vues dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [Perspectives](../multidimensional-models-olap-logical-cube-objects/perspectives.md).  
  
 Pour créer ou modifier les perspectives d’un cube, utilisez l’onglet **Perspectives** dans le Concepteur de cube. La première colonne de l’onglet **Perspectives** est la colonne **Objets de cube** , qui répertorie tous les objets du cube. Ceci correspond à la perspective par défaut du cube, soit le cube lui-même.  
  
## <a name="creating-or-deleting-perspectives"></a>Création ou suppression de perspectives  
 Vous pouvez ajouter une perspective à l’onglet **Perspectives** en cliquant sur **Nouvelle perspective** dans le menu **Cube** . Vous pouvez aussi cliquer sur le bouton **Nouvelle perspective** de la barre d’outils ou cliquer avec le bouton droit à un endroit quelconque du volet, puis cliquer sur **Nouvelle perspective** dans le menu contextuel. Vous pouvez ajouter un nombre illimité de perspectives à un cube.  
  
 Pour supprimer une perspective, cliquez d'abord sur une cellule de la colonne de la perspective à supprimer. Ensuite, dans le menu **Cube** , cliquez sur **Supprimer la perspective**. Vous pouvez aussi cliquer sur le bouton **Supprimer la perspective** de la barre d’outils ou cliquer avec le bouton droit sur une cellule de la perspective à supprimer, puis cliquer sur **Supprimer la perspective** dans le menu contextuel.  
  
## <a name="renaming-perspectives"></a>affectation d'un nouveau nom aux perspectives  
 La première ligne de chaque perspective affiche son nom. Lorsque vous créez une perspective, son nom initial est Perspective (suivi d'un nombre ordinal, commençant par 1, s'il existe déjà une perspective nommée Perspective). Vous pouvez cliquer sur le nom pour le modifier.  
  
## <a name="hiding-objects-from-a-perspective"></a>Masquage des objets dans une perspective  
 Pour masquer un objet dans une perspective, désactivez la case à cocher dans la ligne qui correspond à l'objet dans la colonne de la perspective. Les objets de cube qui peuvent être masqués dans une perspective sont les suivants :  
  
-   les groupes de mesures ;  
  
-   Mesures  
  
-   Dimensions  
  
-   Hiérarchies  
  
-   Les jeux nommés  
  
-   Indicateurs de performance clés  
  
-   Actions  
  
-   Membres calculés  
  
 Pour afficher un objet, développez la catégorie (**Groupes de mesures**, **Dimensions**, **Indicateurs de performance clés**, **Calculs**ou **Actions**) pour n’importe quel type d’objet sous **Objets de cube**. Pour afficher les hiérarchies ou les attributs d’une dimension, développez d’abord une dimension, puis la ligne **Hiérarchies** ou **Attributs** . Pour afficher les mesures d'un groupe de mesures, développez ce dernier.  
  
## <a name="see-also"></a>Voir aussi  
 [Cubes dans les modèles multidimensionnels](cubes-in-multidimensional-models.md)  
  
  
