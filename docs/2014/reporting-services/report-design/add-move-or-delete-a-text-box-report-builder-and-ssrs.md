---
title: Ajouter, déplacer ou supprimer une zone de texte (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49ba35fb0ecb5ed70fe737a10ce9a700d4e4c816
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106584"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a>Ajouter, déplacer ou supprimer une zone de texte (Générateur de rapports et SSRS)
  Les zones de texte sont les éléments de rapport les plus couramment utilisés dans les rapports. Vous pouvez ajouter une zone de texte au corps du rapport pour afficher des informations telles que les titres, les choix de paramètres, les champs prédéfinis et les dates.  
  
 Chaque cellule dans une table ou une matrice est réellement une zone de texte. Les données affichées dans un rapport avec des tables et des matrices sont presque toutes le fruit de l'évaluation par le processeur de rapports du contenu de chaque zone de texte du rapport. De ce fait, vous pouvez mettre en forme des cellules de la même façon que d'autres zones de texte en dehors de la région de données.  
  
 Pour ajouter une zone de texte à une région de données de liste, vous devez d'abord ajouter la zone de texte, puis la faire glisser vers la liste.  
  
> [!NOTE]  
>  Lorsque vous cliquez sur une zone de texte, vous modifiez immédiatement le texte contenu dans la zone de texte. Pour sélectionner la zone de texte en elle-même et non le texte contenue dans celle-ci, appuyez sur Échap.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-text-box"></a>Pour ajouter une zone de texte  
  
1.  Sous l'onglet **Insérer** en mode Conception, cliquez sur **Zone de texte**.  
  
2.  Cliquez sur l'aire de conception, puis faites glisser la souris pour créer une zone de la taille voulue pour la zone de texte. Une autre solution consiste à cliquer sur l'aire de conception pour créer une zone de texte de taille par défaut.  
  
### <a name="to-add-a-text-box-in-a-list"></a>Pour ajouter une zone de texte dans une liste  
  
1.  Sous l'onglet **Insérer** en mode création de rapport, cliquez sur **Liste**.  
  
2.  Cliquez sur l'aire de conception, puis faites glisser la souris pour créer une zone de la taille voulue pour la liste. Une autre solution consiste à cliquer sur l'aire de conception pour créer une liste de taille par défaut.  
  
3.  Sous l'onglet **Insérer** , cliquez sur **Zone de texte**.  
  
4.  Sur l'aire de conception, cliquez et faites glisser la souris pour créer une zone de la taille voulue pour la zone de texte dans la liste ajoutée à l'étape 1. Une autre solution consiste à cliquer sur l'aire de conception dans la liste pour créer une zone de texte de taille par défaut.  
  
5.  Pour vérifier que la zone de texte est correctement imbriquée dans la liste, sélectionnez la zone de texte.  
  
    > [!NOTE]  
    >  Si vous cliquez dans la zone de texte en mode édition, appuyez sur Échap pour sélectionner la zone de texte.  
  
6.  Dans le volet Propriétés, vérifiez que la propriété **Parent** est le rectangle qui été automatiquement ajouté à la région de données de la liste.  
  
    > [!NOTE]  
    >  Si le volet Propriétés n’est pas visible, cochez **Propriétés** sous l’onglet **Affichage** .  
  
### <a name="to-move-a-text-box"></a>Pour déplacer une zone de texte  
  
1.  En mode création de rapport, cliquez sur un espace vide à l'intérieur de la zone de texte pour la sélectionner.  
  
    > [!NOTE]  
    >  Si vous cliquez dans la zone de texte en mode édition, appuyez sur Échap pour sélectionner la zone de texte.  
  
2.  Cliquez sur la poignée de la zone de texte et faites glisser la zone de texte vers le nouvel emplacement. Vous pouvez également utiliser les touches de direction pour déplacer une zone de texte sélectionnée horizontalement ou verticalement. Pour déplacer la zone de texte par incréments plus petits sur l'aire de conception, maintenez la touche CTRL enfoncée et utilisez les touches de direction.  
  
### <a name="to-delete-a-text-box"></a>Pour supprimer une zone de texte  
  
1.  En mode création de rapport, cliquez avec le bouton droit sur un espace vide à l’intérieur de la zone de texte pour la sélectionner, puis cliquez sur **Supprimer**. Une autre solution consiste à cliquer sur un espace vide à l'intérieur de la zone de texte, puis à appuyer sur Suppr.  
  
    > [!NOTE]  
    >  Si vous cliquez dans la zone de texte en mode édition, appuyez sur Échap pour sélectionner la zone de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Zones de texte &#40;Générateur de rapports et SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Raccourcis clavier &#40;Générateur de rapports&#41;](../report-builder/keyboard-shortcuts-report-builder.md)  
  
  
