---
title: Modification des noms de tables par défaut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b6e43196f5bc318630a52073e22969dc58a0e64a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079230"
---
# <a name="modifying-default-table-names"></a>Modification des noms de tables par défaut
  Vous pouvez modifier la valeur de la propriété **FriendlyName** des objets de la vue de source de données pour en faciliter l'utilisation et la compréhension.  
  
 Au cours de la tâche suivante, vous allez modifier le nom de chaque table dans la vue de source de données en supprimant les préfixes «**Dim**» et «**Fact**» de ces tables. Cela rendre le cube et les objets de la dimension (que vous allez définir dans la leçon suivante) plus faciles à comprendre et à utiliser.  
  
> [!NOTE]  
>  Vous pouvez également modifier les noms des colonnes, définir des colonnes calculées et joindre des tables ou des vues dans la vue de source de données pour en faciliter l'utilisation.  
  
### <a name="to-modify-the-default-name-of-a-table"></a>Pour modifier le nom par défaut d'une table  
  
1.  Dans le volet **Tables** du **Concepteur de source de données**, cliquez avec le bouton droit sur la table **FactInternetSales** , puis cliquez **Propriétés**.  
  
2.  Si la fenêtre Propriétés à droite de la fenêtre Microsoft Visual Studio ne s'affiche pas, cliquez sur le bouton **Masquer automatiquement** dans la barre de titre de la fenêtre Propriétés afin que cette fenêtre reste visible.  
  
     Il est plus facile de modifier les propriétés de chaque table dans la vue de source de données si la fenêtre des propriétés reste ouverte. Si vous n'ouvrez pas la fenêtre en utilisant le bouton **Masquer automatiquement** , elle se ferme lorsque vous cliquez sur un autre objet dans le volet **Diagramme** .  
  
3.  Modifiez la propriété **FriendlyName** de l’objet **FactInternetSales** en *`InternetSales`*.  
  
     Lorsque vous cliquez en dehors de la cellule correspondant à la propriété **FriendlyName** , la modification est appliquée. Dans la leçon suivante, vous définirez un groupe de mesures basé sur cette table de faits. Le nom de la table de faits sera InternetSales au lieu de FactInternetSales à cause de la modification que vous avez apportée dans cette leçon.  
  
4.  Cliquez sur **DimProduct** dans le volet **Tables** . Dans la Fenêtre Propriétés, remplacez la **FriendlyName** valeur de la *`Product`* propriété FriendlyName par.  
  
5.  Modifiez la propriété **FriendlyName** de chaque table restante dans la vue de source de données en procédant de la même façon, pour supprimer le préfixe «**Dim**».  
  
6.  Une fois terminé, cliquez sur le bouton **Masquer automatiquement** pour masquer à nouveau la fenêtre des propriétés.  
  
7.  Dans le menu **Fichier** , ou dans la barre d'outils de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur **Enregistrer tout** pour enregistrer les modifications vous avez faites à ce stade dans le projet Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Vous pouvez arrêter le didacticiel ici si vous le souhaitez et le reprendre ultérieurement.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Définition et déploiement d'un cube](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Modifier les propriétés d’une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
