---
title: Éditeur de formulaire d’action (onglet Actions, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.action.f1
ms.assetid: c363a29b-6099-473c-9625-460cc15b3d95
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7c0a9b232a30fbaa4358bf9b23eb28ff16d79b2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062957"
---
# <a name="action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Éditeur de formulaire d'action (onglet Actions, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet Éditeur de formulaire d’action sous l’onglet **Actions** dans le Concepteur de cube pour créer et modifier des actions standard.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de l'action.  
  
 **Cible d'action**  
 Développez pour afficher les options **Type de cible** et **Objet cible** .  
  
 **Type de cible**  
 Sélectionnez le type d'objet auquel l'action doit être associée. Le serveur retourne au client uniquement les actions qui s'appliquent à l'objet du type spécifié. L’action est disponible pour le client si la **Condition** est remplie et si les objets spécifiés dans le tableau suivant sont sélectionnés.  
  
|Value|Objet sélectionné|  
|-----------|---------------------|  
|Membres d'attribut|Un membre est sélectionné d’après un niveau qui dépend de l’attribut **Objet cible**.|  
|Cellules|L’ensemble nommé dans **Objet cible** est sélectionné. Sélectionnez **Toutes les cellules** pour sélectionner toutes les cellules du cube.|  
|Cube|Le cube dans **Objet cible** est sélectionné. Sélectionnez CURRENTCUBE pour utiliser le cube actif.<br /><br /> Remarque : À l’aide de CURRENTCUBE fournit la portabilité supplémentaire dans les cas où le cube peut être renommé ou l’action copiée dans d’autres cubes. Il est recommandé d'utiliser l'option CURRENTCUBE pour représenter le cube actif.|  
|Membres de dimension|Un membre de la dimension dans **Objet cible** est sélectionné.|  
|Hierarchy|La hiérarchie dans **Objet cible** est sélectionnée.|  
|Membres de hiérarchie|Un membre de la hiérarchie dans **Objet cible** est sélectionné.|  
|Level|Le niveau dans **Objet cible** est sélectionné.|  
|Membres de niveau|Un membre du niveau dans **Objet cible** est sélectionné.|  
  
 **Objet cible**  
 Sélectionnez l'objet auquel l'action doit être associée. L’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retourne au client uniquement les actions qui s’appliquent à l’objet sélectionné. La liste des objets disponibles est conditionnée par le choix du **Type de cible**.  
  
 **Condition (facultatif)**  
 Entrez l’expression MDX (Multidimensional Expressions) décrivant une condition facultative utilisée en combinaison avec **Objet cible**qui impose une limite supplémentaire sur le moment où l’action est disponible. L'expression doit retourner une valeur booléenne qui, si elle est vraie, indique que l'action est disponible.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 **Contenu d'action**  
 Développez pour afficher les options **Type** et **Expression d’action** .  
  
 **Type**  
 Sélectionnez le type d'action à effectuer lorsque l'action est exécutée. Les types d'actions suivants sont disponibles :  
  
|Value|Description|  
|-----------|-----------------|  
|Dataset|Retourne une instruction MDX (Multidimensional Expressions) qui représente un jeu de données multidimensionnel que l'application cliente doit exécuter et afficher.|  
|Propriétaire|Retourne une chaîne propriétaire que peuvent interpréter les applications clientes associées au paramètre **Application** de cette action.|  
|Ensemble de lignes|Retourne une instruction MDX (Multidimensional Expressions) qui représente un ensemble de lignes tabulaire que l'application cliente doit exécuter et afficher.|  
|.|Retourne une chaîne de commande que l'application cliente doit exécuter.|  
|URL|Retourne une chaîne d'adresse URL (Uniform Resource Location) que l'application cliente doit ouvrir, en utilisant généralement navigateur Internet.|  
  
 Pour plus d’informations sur les types d’actions, consultez [Actions &#40;Analysis Services - Données multidimensionnelles&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
 **Expression d’action**  
 Tapez l'expression MDX (Multidimensional Expressions) qui retourne dans l'application cliente la chaîne de caractères retournée par l'action pour exécution.  
  
 **Propriétés supplémentaires**  
 Développez pour afficher les options **Invocation**, **Application**, **Description**, **Légende**et **La légende est MDX** .  
  
 **Invocation**  
 Sélectionnez le paramètre qui indique le moment où l'action doit être effectuée.  
  
> [!NOTE]  
>  Cette option ne fournit qu'une recommandation à une application cliente quant au moment d'exécution d'une action ; elle ne commande pas directement l'appel de l'action.  
  
 Le tableau suivant décrit les paramètres disponibles.  
  
|Value|Description|  
|-----------|-----------------|  
|Traitement|L’action doit s’exécuter dans le cadre d’une opération par lot ou d’une tâche [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .|  
|Interactif|L'action s'exécute lorsque l'utilisateur l'invoque.|  
|À l’ouverture|L'action s'exécute à la première ouverture du cube.|  
  
 **Application**  
 Entrez le nom de l’application qui peut interpréter la chaîne retournée par **Expression d’action**.  
  
 Vous pouvez également utiliser cette option pour identifier l'application cliente qui utilise le plus souvent cette action, ainsi que pour afficher les icônes appropriées dans un menu contextuel à côté de l'action.  
  
> [!NOTE]  
>  Cette option ne fournit qu'une recommandation à une application cliente quant à l'application cliente qui doit exécuter une action ; elle ne commande pas directement l'accès à l'action. Les applications clientes doivent masquer toute action associée à d'autres applications clientes.  
  
 **Description**  
 Tapez une description facultative de l'action.  
  
 **Légende**  
 Entrez la légende à afficher pour l’action dans l’application cliente si l’option **La légende est MDX** a la valeur **False**.  
  
 Entrez l’expression MDX (Multidimensional Expressions) qui retourne une chaîne pour la légende si l’option **La légende est MDX** a la valeur **True**.  
  
 **La légende est MDX**  
 Sélectionnez **False** pour indiquer que la **Légende** contient une chaîne littérale qui représente une légende à afficher pour l’action dans l’application cliente.  
  
 Sélectionnez **True** pour indiquer que la **Légende** contient une expression MDX qui retourne une chaîne représentant une légende à afficher pour l’action dans l’application cliente. L'expression MDX doit être résolue avant que l'action soit retournée à l'application cliente.  
  
## <a name="see-also"></a>Voir aussi  
 [Actions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Organisateur d’action &#40;onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Outils de calcul &#40;onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire d’Action d’extraction &#40;onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Report Action Form Editor &#40;onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
