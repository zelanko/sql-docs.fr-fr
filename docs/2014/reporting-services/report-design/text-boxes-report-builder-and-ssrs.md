---
title: Zones de texte (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10134"
- sql12.rtp.rptdesigner.textproperties.general.f1
- "10120"
- sql12.rtp.rptdesigner.textboxproperties.general.f1
ms.assetid: df49e4e3-f279-4c63-a03b-b70c095f4ba2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66dadc7a6163b8da7024818a9ecee16d5b3df696
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029300"
---
# <a name="text-boxes-report-builder-and-ssrs"></a>Zones de texte (Générateur de rapport et SSRS)
  Lorsque vous pensez à une zone de texte, vous pensez probablement à une zone autonome qui contient le texte sur une surface comme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint. Dans le Générateur de rapports, certaines zones de texte sont comme cela et elles peuvent afficher le texte littéral pour les titres, les descriptions et les étiquettes, ou du texte dynamique basé sur des expressions. Toutefois, chaque cellule d'une table ou matrice (région de données de tableau matriciel) contient également une zone de texte, qui peut être mise en forme de la même manière que les zones de texte autonomes de votre rapport.  
  
> [!NOTE]  
>  Si vous faites glisser une valeur de champ de dataset de rapport directement vers l'aire de conception ou vers une zone de texte de l'aire de conception du rapport, seule la première valeur du jeu de résultats est visible lorsque vous exécutez le rapport. Pour voir toutes les valeurs d'un champ, vous devez faire glisser le champ vers une cellule dans une table ou une matrice. Ainsi, lorsque vous exécuterez le rapport, vous verrez toutes les valeurs dans ce champ.  
  
 Pour afficher du texte récurrent dans une disposition de forme libre, placez une zone de texte dans une région de données de liste. Utilisez une liste lorsque vous souhaitez répéter un formulaire pour plusieurs valeurs, par exemple une facture client utilisée une seule fois pour chaque client. Pour plus d’informations, consultez [répertorie &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
 Utilisez un conteneur rectangle lorsque vous souhaitez contrôler la disposition des zones de texte et l'espace blanc en dessous de la dernière zone de texte. Pour plus d’informations, consultez [Rectangles et lignes &#40;Générateur de rapports et SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md).  
  
 Les expressions dans une zone de texte peuvent contenir du texte littéral, pointer vers un champ de la base de données ou calculer des données. Toutes les expressions sont affichées sous la forme de texte d'espace réservé de sorte que vous pouvez mettre en forme des nombres, des couleurs et d'autres propriétés d'apparence. Vous pouvez également combiner des espaces réservés avec le texte littéral dans la même zone de texte.  
  
 Vous pouvez mettre en forme le texte dans toute zone de texte unique en utilisant plusieurs polices, couleurs, styles et actions. Pour plus d’informations, consultez [Mise en forme du texte et des espaces réservés &#40;Générateur de rapports et SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="GrowShrinkTextBox"></a> Agrandissement et réduction d'une zone de texte  
 Par défaut, les zones de texte ont une taille fixe. Vous pouvez autoriser la réduction ou l'agrandissement d'une zone de texte de manière verticale en fonction de son contenu. Pour plus d’informations, consultez [Autoriser l’agrandissement ou la réduction d’une zone de texte &#40;Générateur de rapports et SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md).  
  
## <a name="orienting-a-text-box"></a>Orientation d'une zone de texte  
 L'orientation des zones de texte peut vous aider à créer des rapports plus lisibles, à prendre en charge l'orientation de texte spécifique aux paramètres régionaux, à ajuster plus de colonnes dans un rapport imprimé qui a une taille de page fixe et à créer des rapports avec un contenu plus graphique. Une zone de texte peut être orientée dans différentes directions : horizontalement, verticalement ou avec une rotation de 270 degrés. L'option verticale est utilisée le plus communément pour les langues asiatiques qui sont écrites de haut en bas. Dans la plupart des convertisseurs, l'option verticale gère la propriété de rotation du glyphe afin que le texte soit écrit de haut en bas, mais les caractères ne figurent pas sur leurs côtés. Pour d'autres langues, le texte orienté verticalement et selon une rotation à 270 degrés est écrit obliquement.  
  
 Vous pouvez appliquer une orientation aux zones de texte qui contiennent du texte littéral, des champs d'un dataset de rapport ou des données calculées. La zone de texte peut être autonome dans le corps du rapport, dans une table ou matrice, ou dans un en-tête ou pied de page de rapport.  
  
 L'image suivante affiche trois versions d'un rapport de tableau qui regroupe des données par mois. La zone de texte qui contient la valeur de mois utilise une orientation de zone de texte différente.  
  
 ![rs_TextBoxOrientation](../media/rs-textboxorientation.gif "rs_TextBoxOrientation")  
  
 L'orientation est définie sur la zone de texte et s'applique à tout le texte de la zone. Vous ne pouvez pas spécifier d'orientation différente pour certaines parties de la zone de texte.  
  
 Pour rapidement commencer à modifier l’orientation du texte, consultez la section sur la rotation du texte dans le [didacticiel : Mettre en forme du texte &#40;Générateur de rapports&#41;](../tutorial-format-text-report-builder.md). Pour plus d’informations, consultez [définir l’Orientation de zone de texte &#40;Générateur de rapports et SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md).  
  
##  <a name="HowTo"></a> Rubriques de procédures  
 [Ajouter, déplacer ou supprimer une zone de texte &#40;Générateur de rapports et SSRS&#41;](add-move-or-delete-a-text-box-report-builder-and-ssrs.md)  
  
 [Mettre en forme du texte dans une zone de texte &#40;Générateur de rapports et SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
 [Définir l’orientation d’une zone de texte &#40;Générateur de rapports et SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md)  
  
 [Autoriser l’agrandissement ou la réduction d’une zone de texte &#40;Générateur de rapports et SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme du texte et des espaces réservés &#40;Générateur de rapports et SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Mise en forme des nombres et des dates &#40;Générateur de rapports et SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md)  
  
  
