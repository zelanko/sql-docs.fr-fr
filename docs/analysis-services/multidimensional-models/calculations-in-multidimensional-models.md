---
title: "Calculs dans les mod&#232;les multidimensionnels | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "calculs [Analysis Services], création"
  - "suppression de calculs"
  - "calculs [Analysis Services], scripts"
  - "Concepteur de cube"
  - "modification de scripts"
  - "retrait de calculs"
  - "calculs [Analysis Services], suppression"
  - "scripts [Analysis Services], calculs"
  - "cubes [Analysis Services], calculs"
  - "ordres de résolution [Analysis Services]"
ms.assetid: c21b3459-9bef-45a2-aba5-c992eba5b66e
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# Calculs dans les mod&#232;les multidimensionnels
  Utilisez l’onglet **Calculs** du Concepteur de cube pour créer des membres calculés, des jeux nommés et d’autres calculs MDX (Multidimensional Expressions).  
  
 L’onglet **Calculs** contient les trois volets suivants :  
  
-   Le volet **Organisateur de script** répertorie les calculs présents dans un cube. Utilisez ce volet pour créer, organiser et sélectionner des calculs à modifier.  
  
-   Le volet **Outils de calcul** fournit des métadonnées, des fonctions et des modèles que vous pouvez utiliser pour créer des calculs.  
  
-   Le volet des expressions de calcul prend en charge un mode Formulaire et un mode Script.  
  
> [!NOTE]  
>  Pour plus d’informations sur la génération de scripts MDX, consultez [Introduction aux scripts MDX dans Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892) et consultez la section Ressources supplémentaires de la page [SQL Server 2005 – Analysis Services](http://go.microsoft.com/fwlink/?LinkId=80853) du site web Microsoft TechNet. Pour plus d’informations sur les problèmes de performance liés à la conception de cubes, consultez le [Guide des performances SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## Création d'un nouveau calcul  
 Pour créer un calcul, sous l’onglet **Calculs** du Concepteur de Cube, dans le menu **Cube**, cliquez sur **Nouveau membre calculé**, **Nouveau jeu nommé** ou **Nouvelle commande de script**, en fonction du type de calcul à créer. Vous pouvez également soit cliquer sur l’un des boutons correspondants dans la barre d’outils, soit cliquer avec le bouton droit n’importe où dans le volet **Organisateur de script** et cliquer ensuite sur l’une des commandes du menu contextuel. Cette action ajoute un nouveau calcul au volet **Organisateur de script** et affiche les champs correspondants dans le formulaire de calcul dans le volet des expressions de calcul. Si vous créez un nouveau script, cette action ouvre le mode Script dans le volet des expressions de calcul. Pour plus d’informations sur la création des trois types de calculs, consultez [Créer des membres calculés](../../analysis-services/multidimensional-models/create-calculated-members.md), [Créer des jeux nommés](../../analysis-services/multidimensional-models/create-named-sets.md) et [Définir des attributions et d’autres commandes de script](../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md).  
  
## Modification des scripts  
 Pour modifier des scripts, utilisez le volet des expressions de calcul de l’onglet **Calculs**. Le volet des expressions de calcul propose deux modes d'affichage : un mode Script et un mode Formulaire. Le mode Formulaire affiche les expressions et les propriétés d'une commande unique. Lorsque vous modifiez un script MDX, une zone d'expression remplit entièrement la vue Formulaire.  
  
 Le mode Script fournit un éditeur de code dans lequel vous pouvez modifier les scripts. Tant que le volet des expressions de calcul est en mode Script, le volet **Organisateur de script** est masqué. Le mode Script offre un codage en couleurs, un appariement des parenthèses, une saisie semi-automatique et des régions de code MDX. Les régions de code MDX peuvent être réduites ou développées pour faciliter la modification.  
  
 Pour basculer entre le mode Formulaire et le mode Script, cliquez sur le menu **Cube**, pointez sur **Afficher les calculs dans**, puis cliquez sur **Script** ou **Formulaire**. Vous pouvez également cliquer sur **Mode Formulaire** ou **Mode Script** dans la barre d’outils.  
  
## Modification de l'ordre de résolution  
 Les calculs sont résolus dans l’ordre indiqué dans le volet **Organisateur de script**. Vous pouvez modifier l’ordre des calculs en cliquant avec le bouton droit sur le calcul de votre choix, puis en cliquant sur **Monter** ou **Descendre** dans le menu contextuel. Vous pouvez également cliquer sur un calcul et cliquer ensuite sur le bouton **Monter** ou **Descendre** de la barre d’outils.  
  
 Vous pouvez remplacer cet ordre manuellement pour les cellules calculées et les membres calculés. Pour plus d’informations sur l’ordre de test et l’ordre de résolution, consultez [Présentation des concepts d’ordre de passage et d’ordre de résolution &#40;MDX&#41;](../../analysis-services/multidimensional-models/mdx/understanding-pass-order-and-solve-order-mdx.md).  
  
## Suppression d'un calcul  
 Pour supprimer un calcul existant, dans le volet **Organisateur de script** de l’onglet **Calculs**, sélectionnez le calcul à supprimer, puis cliquez sur **Supprimer** dans le menu **Edition** ou cliquez sur l’icône **Supprimer** de la barre d’outils. Vous pouvez aussi cliquer avec le bouton droit sur le calcul dans le volet **Organisateur de script** et sélectionner **Supprimer** dans le menu contextuel.  
  
  