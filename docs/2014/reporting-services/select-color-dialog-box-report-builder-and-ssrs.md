---
title: Boîte de dialogue Sélectionner une couleur (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.selectcolor.f1
- "10090"
helpviewer_keywords:
- Select Color dialog box
ms.assetid: ac7089a3-5c7b-4f53-8348-180610e86da2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6bcbbe828da811ace5df4feea5cfdf888e1e6ca5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66101381"
---
# <a name="select-color-dialog-box-report-builder-and-ssrs"></a>Boîte de dialogue Sélectionner une couleur (Générateur de rapports et SSRS)
  Utilisez la boîte de dialogue **Sélectionner une couleur** pour spécifier les options de couleur d'un graphique ou de l'arrière-plan d'une cellule ou de plusieurs cellules dans une région de données ou une zone de texte.  
  
## <a name="options"></a>Options  
 **Sélecteur de couleurs**  
 Choisissez une option parmi les trois proposées permettant de spécifier la façon dont vous souhaitez sélectionner des couleurs :  
  
-   **Sélecteur - Cercle de couleur** Choisissez une couleur à l’aide des valeurs de couleur Teinte/Saturation/Luminosité (TSL).  
  
-   **Sélecteur - Carré de couleur** Choisissez une couleur à l’aide des valeurs de couleur Rouge/Vert/Bleu (RVB).  
  
-   **Palette - Couleurs standard** Choisissez une couleur dans une liste prédéfinie de valeurs de couleur.  
  
 **Cercle de couleur**  
 Utilisez cette option pour les couleurs TSL, car les valeurs TSL sont associées à un système de coordonnées cylindriques. La teinte représente la couleur réelle, la saturation correspond à la pureté de la couleur et la luminosité est la luminosité ou l'obscurité relative.  
  
 Lorsque vous sélectionnez une couleur, le centre du cercle détermine la couleur. Utilisez le curseur de couleur pour modifier la teinte. Les coordonnées x et y représentent respectivement les valeurs de saturation et de luminosité.  
  
 **Carré de couleur**  
 Utilisez cette option pour les couleurs RVB, car les valeurs RVB sont associées à un système de coordonnées cartésiennes. R est la valeur pour le rouge, V est la valeur pour le vert et B, la valeur pour le bleu.  
  
 Lorsque vous sélectionnez une couleur, le centre du carré détermine la couleur. Utilisez le curseur de couleur pour modifier la plage de la couleur choisie. Les coordonnées x et y représentent les deux autres couleurs. Par exemple, si vous sélectionnez le vert, le curseur affiche la plage des valeurs vertes, tandis que les coordonnées x et y représentent respectivement les valeurs rouges et bleues.  
  
 **Couleurs standard**  
 Utilisez pour les couleurs nommées [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` de l’énumération.  
  
 **Système de couleurs**  
 Spécifiez des couleurs RVB ou TSL. Ce choix modifie l'affichage pour afficher des valeurs RVB ou TSL, mises à jour de façon interactive lorsque vous utilisez un cercle de couleur ou un carré de couleur pour le **Sélecteur de couleurs**.  
  
 La valeur **Alpha** s'affiche pour certaines propriétés lorsqu'une couleur peut inclure une valeur de transparence, par exemple pour un remplissage de série de graphique. Pour les propriétés qui ne prennent pas en charge la transparence, cette valeur est désactivée.  
  
 **Rouge**  
 Valeur décimale pour la composante rouge de la couleur RVB. Utilisez la zone de sélection numérique pour modifier la valeur ou tapez une valeur comprise entre 0 et 255.  
  
 **Vert**  
 Valeur décimale pour la composante verte de la couleur RVB. Utilisez la zone de sélection numérique pour modifier la valeur ou tapez une valeur comprise entre 0 et 255.  
  
 **Bleu**  
 Valeur décimale pour la composante bleue de la couleur RVB. Utilisez la zone de sélection numérique pour modifier la valeur ou tapez une valeur comprise entre 0 et 255.  
  
 **Alpha**  
 Valeur décimale pour la composante alpha ou de transparence de la couleur. Lorsque cette valeur est activée, vous pouvez utiliser le commutateur de curseur pour ajuster le degré de transparence voulu.  
  
 **Teinte**  
 Valeur décimale pour la teinte de la couleur TSL. Utilisez la zone de sélection numérique pour modifier la valeur ou tapez une valeur comprise entre 0 et 255.  
  
 **Saturation**  
 Valeur décimale pour la saturation de la couleur TSL. Utilisez la zone de sélection numérique pour modifier la valeur ou tapez une valeur comprise entre 0 et 255.  
  
 **Brightness (Luminosité)**  
 Valeur décimale pour la luminosité de la couleur TSL. Utilisez la zone de sélection numérique pour modifier la valeur ou tapez une valeur comprise entre 0 et 255.  
  
 **Échantillon de couleur**  
 Affiche la couleur actuelle dans la partie gauche du volet et affiche interactivement la nouvelle couleur que vous choisissez dans la partie droite du volet. S'il n'existe pas de couleur par défaut, la partie gauche du volet est blanche. La plupart des propriétés RDL n'ont aucune couleur par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des éléments de rapport &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Mise en forme du texte et des espaces réservés &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  
