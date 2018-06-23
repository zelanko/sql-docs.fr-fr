---
title: Ajouter un signet à un rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f130562e-5673-40e3-8e01-de7227a21d41
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: c5dbb01a671b6490c798ec9e688a6824efdf122a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154334"
---
# <a name="add-a-bookmark-to-a-report-report-builder-and-ssrs"></a>Ajouter un signet à un rapport (Générateur de rapports et SSRS)
  Ajoutez des signets et des liens de signet à un rapport lorsque vous souhaitez fournir une table des matières personnalisée ou des liens de navigation interne personnalisés dans le rapport. En général, vous ajoutez des signets aux emplacements du rapport où vous souhaitez amener les utilisateurs, comme les tables ou graphiques, ou les valeurs de groupe uniques qui figurent dans une table ou une matrice. Vous pouvez créer vos propres chaînes à utiliser en tant que signets, ou, pour les groupes, vous pouvez définir le signet sur l'expression de groupe.  
  
 Une fois que vous avez créé des signets, vous pouvez ajouter des éléments de rapport sur lesquels l'utilisateur peut cliquer pour atteindre chaque signet. Ces éléments sont souvent des zones de texte ou des images.  
  
 Par exemple, si votre rapport affiche une table dans laquelle un regroupement par couleur a été effectué, vous pouvez ajouter à l'en-tête de groupe un signet basé sur l'expression de groupe. Vous pouvez ensuite ajouter au début du rapport une table avec une seule zone de texte qui affiche les couleurs et définir le lien de signet vers cette zone de texte. Lorsque vous cliquez sur la couleur, le rapport accède à la page qui affiche la ligne d'en-tête de groupe correspondant à cette couleur.  
  
 Vous pouvez ajouter un signet à tout élément de rapport et ajouter un lien de signet à tout élément assorti d'une propriété **Action** , par exemple, une zone de texte, une image ou une série calculée dans un graphique. Pour plus d’informations, consultez [Boîte de dialogue Propriétés relatives aux actions &#40;Générateur de rapports et SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-bookmark"></a>Pour ajouter un signet  
  
1.  En mode création de rapport, sélectionnez la zone de texte, l'image, le graphique ou un autre élément de rapport auquel ajouter un signet. Les propriétés de l'élément sélectionné s'affichent dans le volet Propriétés.  
  
2.  Dans la zone de texte située en regard de **Signet**, tapez une chaîne qui constituera l'étiquette de ce signet. Par exemple, vous pouvez taper **PhotoVélo** comme signet pour une image de votre rapport. Vous pouvez aussi cliquer sur le bouton Expression (**fx**) pour ouvrir la boîte de dialogue **Expression** et spécifier une expression qui donne une étiquette. Pour un groupe, l'expression que vous tapez doit être l'expression de groupe.  
  
    > [!NOTE]  
    >  Le signet peut être une chaîne quelconque, mais il doit être unique dans le rapport. S'il n'est pas unique, un lien vers celui-ci utilisera le premier signet correspondant.  
  
### <a name="to-add-a-bookmark-link"></a>Pour ajouter un lien de signet  
  
1.  En mode Conception, cliquez avec le bouton droit sur la zone de texte, l’image ou le graphique auquel vous voulez ajouter un lien, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés** de cet élément de rapport, cliquez sur **Action**.  
  
3.  Sélectionnez **Atteindre le signet**. Une section supplémentaire apparaît dans la boîte de dialogue pour cette option.  
  
4.  Dans la zone **Sélectionnez un signet** , tapez ou sélectionnez un signet ou une expression qui est évaluée en signet. À l'aide de l'exemple précédent, tapez **PhotoVélo** pour créer un lien vers l'image dans votre rapport.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  (Facultatif) Le texte n'est pas mis en forme automatiquement comme un lien. Pour le texte, il est utile de modifier la couleur et l'effet du texte pour indiquer qu'il s'agit d'un lien. Par exemple, changez la couleur en bleu et l'effet en soulignement dans la section **Police** sous l'onglet Accueil du ruban.  
  
7.  Pour tester le lien, cliquez sur **Exécuter** afin d'afficher l'aperçu du rapport, puis cliquez sur l'élément de rapport sur lequel vous avez défini ce lien.  
  
## <a name="see-also"></a>Voir aussi  
 [Tri interactif, Explorateurs de documents et liens &#40;Générateur de rapports et SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Filtrer, regrouper et trier les données &#40;rapport Générateur et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  