---
title: Attribut de boîte de dialogue traduction de données (Analysis Services - données multidimensionnelles) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dimensiondesigner.dimensionstoragesettings.f1
helpviewer_keywords:
- Attribute Data Translation dialog box
ms.assetid: bed286de-1e9b-49de-b09e-3cd076aba152
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1b8d7f28696e04045ca5ac3f11bf38d4c67f60c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140411"
---
# <a name="attribute-data-translation-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Traduction de données d'attribut (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Traduction de données d’attribut** pour configurer la colonne qui contient les données de sous-titre de traduction, ainsi que l’ordre de classement et de tri à utiliser avec les données traduites. Pour afficher la boîte de dialogue **Traduction de données d’attribut** , vous pouvez :  
  
-   soit cliquer sur **Nouvelle colonne de légende** ou **Modifier la colonne de légende** dans le volet **Barre d’outils** de l’onglet **Traductions** du **Concepteur de dimensions**;  
  
-   soit cliquer avec le bouton droit sur le volet des **détails des traductions** de l’onglet **Traductions** du **Concepteur de dimensions** et sélectionner **Nouvelle colonne de légende** ou **Modifier la colonne de légende**.  
  
## <a name="options"></a>Options  
 **Attribute**  
 Affiche l'attribut sélectionné.  
  
 **Langage**  
 Affiche la langue sélectionnée.  
  
 **Légende traduite**  
 Configure la légende traduite en cours pour l'attribut sélectionné.  
  
 **Colonnes de traduction**  
 Définit la colonne où les données de sous-titre de traduction sont enregistrées. Vous pouvez sélectionner une seule colonne. Toutes les tables associées référencées par la table primaire de dimension sont affichées.  
  
 **Indicateur de classement**  
 Définit l'indicateur de classement pour l'attribut sélectionné. Le classement Windows est sélectionné par défaut. Cliquez sur la flèche vers le bas pour effectuer votre sélection parmi les classements disponibles.  
  
 **Binaire**  
 Sélectionnez cette option pour trier et comparer les données en fonction des modèles des bits définis pour chaque caractère. L'ordre de tri binaire respecte la casse, c'est-à-dire que les minuscules précèdent les majuscules ; il respecte également les accents. Il s'agit de l'ordre de tri le plus rapide.  
  
 Si cette option n'est pas activée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] respecte les règles de tri et de comparaison définies dans les dictionnaires pour la langue ou l'alphabet associé.  
  
> [!NOTE]  
>  Si cette option est sélectionnée, les options **Respecter la casse**, **Respecter les accents**, **Respecter le jeu de caractères Kana**et **Respecter la largeur** sont désactivées.  
  
 **Respect de la casse**  
 Sélectionnez cette option pour trier et comparer les données d'après les règles du dictionnaire de la langue ou de l'alphabet associé et pour faire la distinction entre les majuscules et les minuscules.  
  
 Si cette option n’est pas sélectionnée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère qu’il n’y a pas de différences entre les lettres majuscules et minuscules. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne définit pas si les lettres minuscules doivent être triées avant ou après majuscules les lettres quand **respectant la casse** n’est pas sélectionnée.  
  
 **Avec respect des accents**  
 Sélectionnez cette option pour trier et comparer les données d'après les règles du dictionnaire de la langue ou de l'alphabet associé et pour faire la distinction entre les lettres accentuées ou non. Par exemple, « a » n'est pas équivalent à « á ».  
  
 Si l’option est désactivée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère qu’il n’y a pas de différences entre les lettres accentuées et non accentuées.  
  
 **Kana sensibles**  
 Sélectionnez cette option pour trier et comparer les données d'après les règles du dictionnaire de la langue ou de l'alphabet associé et pour faire la distinction entre les deux types de caractères japonais Kana : Hiragana et Katakana.  
  
 Si l'option est désactivée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère qu'il n'y a pas de différences entre les caractères Hiragana et Katakana.  
  
 **Respecter la largeur**  
 Sélectionnez cette option pour trier et comparer les données d'après les règles du dictionnaire de la langue ou de l'alphabet associé et pour faire la distinction entre un caractère sur un octet (demi-chasse) et le même caractère représenté sur deux octets (pleine chasse).  
  
 Si l'option est désactivée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère qu'il n'y a pas de différences de représentation entre les caractères codés sur un ou deux octets.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Détails des traductions &#40;onglet traductions, Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](translation-details-dimension-designer-analysis-services-multidimensional-data.md)  
  
  