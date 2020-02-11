---
title: Éditeur de formulaire d’action de rapport (onglet actions, concepteur de cube) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.reportaction.f1
ms.assetid: cebfdd07-e376-46d6-86ef-b6f816a2f360
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eeb3df670097c0d511a9f5b779b6705f40a5e897
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070294"
---
# <a name="report-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Éditeur de formulaire d'action de rapport (onglet Actions, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Éditeur de formulaire d’action de rapport** de l’onglet **Actions** dans le Concepteur de cube pour modifier l’action de rapport sélectionnée dans le volet **Organisateur d’action** .  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de l'action.  
  
 **Cible d’action**  
 Développez pour afficher les options **Type de cible** et **Objet cible** .  
  
 **Type de cible**  
 Sélectionnez le type d'objet auquel l'action doit être associée. Le serveur retourne au client uniquement les actions qui s'appliquent à l'objet du type spécifié. L’action est disponible pour le client si la **Condition** est remplie et si les objets spécifiés dans le tableau suivant sont sélectionnés.  
  
|Valeur|Objet sélectionné|  
|-----------|---------------------|  
|Membres d'attribut|Un membre est sélectionné d’après un niveau qui dépend de l’attribut **Objet cible**.<br /><br /> Remarque : les autres hiérarchies des utilisateurs qui utilisent l’attribut sélectionné héritent de l’action de rapport.|  
|Cellules|L’ensemble nommé dans **Objet cible** est sélectionné. Sélectionnez **Toutes les cellules** pour sélectionner toutes les cellules du cube.|  
|Cube|Le cube dans **Objet cible** est sélectionné. Sélectionnez CURRENTCUBE pour utiliser le cube actif.<br /><br /> Remarque : l’utilisation de CURRENTCUBE améliore la portabilité lorsque le cube peut être éventuellement renommé ou l’action copiée dans d’autres cubes. Il est recommandé d'utiliser l'option CURRENTCUBE pour représenter le cube actif.|  
|Membres de dimension|Un membre de la dimension dans **Objet cible** est sélectionné.|  
|Hierarchy|La hiérarchie dans **Objet cible** est sélectionnée.|  
|Membres de hiérarchie|Un membre de la hiérarchie dans **Objet cible** est sélectionné.|  
|Level|Le niveau dans **Objet cible** est sélectionné.|  
|Membres de niveau|Un membre du niveau dans **Objet cible** est sélectionné.|  
  
 **Objet cible**  
 Sélectionnez l'objet auquel l'action doit être associée. L’instance [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retourne au client uniquement les actions qui s’appliquent à l’objet sélectionné. La liste des objets disponibles est conditionnée par le choix du **Type de cible**.  
  
 **Condition (facultatif)**  
 Entrez l’expression MDX (Multidimensional Expressions) décrivant une condition facultative utilisée en combinaison avec **Objet cible**qui impose une limite supplémentaire sur le moment où l’action est disponible. L'expression doit retourner une valeur booléenne qui, si elle est vraie, indique que l'action est disponible.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 **Serveur de rapports**  
 Développez pour afficher les options **Nom du serveur**, **Chemin d’accès au serveur**et **Format de rapport** .  
  
 **Nom du serveur**  
 Tapez le nom de l' [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance sur laquelle l’action exécute le rapport.  
  
 **Chemin du serveur**  
 Tapez le chemin complet d'accès au rapport sur l'instance [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Par exemple, tapez **Sales/YearlySalesByCategory**.  
  
 **Format de rapport**  
 Sélectionnez le format dans lequel le rapport est retourné. Le tableau suivant décrit les formats disponibles.  
  
|Valeur|Description|  
|-----------|-----------------|  
|HTML5|Le rapport est retourné dans format compatible HTML 5.0.|  
|HTML3|Le rapport est retourné dans format compatible HTML 3,2.|  
|Excel|Le rapport est retourné sous la forme d’un fichier de classeur [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel (.xls).|  
|PDF|Le rapport est retourné dans un fichier au format Adobe Portable Document Format (.pdf).|  
  
 **Paramètres (facultatif)**  
 Développez pour afficher une grille dans laquelle il est possible de fournir des paramètres pour le rapport spécifié dans **Rapport**. Cette grille comporte les colonnes suivantes :  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom du paramètre**|Tapez le nom du paramètre à passer au rapport.|  
|**Valeur de paramètre**|Tapez la valeur du paramètre à passer au rapport.<br /><br /> Cliquez sur le bouton de sélection (**...**) pour afficher la boîte de dialogue **Générateur MDX** et créer une expression MDX qui fournit la valeur du paramètre du rapport. Pour plus d’informations sur la boîte de dialogue **Générateur MDX**, consultez [Générateur MDX &#40;Analysis Services – Données multidimensionnelles&#41;](mdx-builder-analysis-services-multidimensional-data.md).<br /><br /> Si le paramètre est défini avec une expression MDX, celle-ci est évaluée lorsque l'action est exécutée ; sinon, elle est passée au rapport sans modification.|  
  
 **Propriétés supplémentaires**  
 Développez pour afficher les options **Invocation**, **Application**, **Description**, **Légende**et **La légende est MDX** .  
  
 **Appel**  
 Sélectionnez le paramètre qui indique le moment où l'action doit être effectuée.  
  
> [!NOTE]  
>  Cette option ne fournit qu'une recommandation à une application cliente quant au moment d'exécution d'une action ; elle ne commande pas directement l'appel de l'action.  
  
 Le tableau suivant décrit les paramètres disponibles.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Batch|L’action doit s’exécuter dans le cadre d’une opération de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] traitement par lot ou d’une tâche.|  
|Interactive|L'action s'exécute lorsque l'utilisateur l'invoque.|  
|À l’ouverture|L'action s'exécute à la première ouverture du cube.|  
  
 **Application**  
 Entrez le nom de l’application qui peut interpréter la chaîne retournée par **Expression d’action**.  
  
 Vous pouvez également utiliser cette option pour identifier l'application cliente qui utilise le plus souvent cette action, ainsi que pour afficher les icônes appropriées dans un menu contextuel à côté de l'action.  
  
> [!NOTE]  
>  Cette option ne fournit qu'une recommandation à une application cliente quant à l'application cliente qui doit exécuter une action ; elle ne commande pas directement l'accès à l'action. Les applications clientes doivent masquer toute action associée à d'autres applications clientes.  
  
 **Description**  
 Tapez une description facultative de l'action.  
  
 **Caption**  
 Entrez la légende à afficher pour l’action dans l’application cliente si l’option **La légende est MDX** a la valeur **False**.  
  
 Tapez l’expression MDX qui retourne une chaîne de caractères pour la légende si l’option **La légende est MDX** a la valeur **True**.  
  
 **La légende est MDX**  
 Sélectionnez **False** pour indiquer que la **Légende** contient une chaîne littérale qui représente une légende à afficher pour l’action dans l’application cliente.  
  
 Sélectionnez **True** pour indiquer que la **Légende** contient une expression MDX qui retourne une chaîne représentant une légende à afficher pour l’action dans l’application cliente. L'expression MDX doit être résolue avant que l'action soit retournée à l'application cliente.  
  
## <a name="see-also"></a>Voir aussi  
 [Actions &#40;le concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Organisateur d’action &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Outils de calcul &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire d’action &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire d’action d’extraction &#40;onglet actions, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
