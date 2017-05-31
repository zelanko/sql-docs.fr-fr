---
title: "Naviguer dans le Concepteur de requêtes et de vues (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- View Designer, navigating
- shortcuts [SQL Server]
- Query Designer [SQL Server], navigating
- keyboard shortcuts [Visual Database Tools]
ms.assetid: 1c65acef-6dfa-463a-bf37-5a5335fe3865
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7cc7f7c8972fae08c956db86f95250d830fba39b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="navigate-in-the-query-and-view-designer-visual-database-tools"></a>Naviguer dans le Concepteur de requêtes et de vues (Visual Database Tools)
Vous pouvez travailler dans le Concepteur de requêtes et de vues en vous servant du clavier ou de la souris. Pour connaître les méthodes spécifiques, consultez les tableaux suivants.  
  
## <a name="any-pane"></a>Tous les volets  
  
|**Pour**|**Appuyez sur**|**Cliquez sur**|  
|----------|-------------|-------------|  
|Vous déplacer entre les volets du Concepteur de requêtes et de vues|F6, Maj+F6|N'importe où dans le volet cible|  
  
> [!TIP]  
> Vous pouvez utiliser les touches de raccourci Ctrl+Tab pour activer d'autres volets en complément des volets du Concepteur de requêtes et de vues.  
  
## <a name="diagram-pane"></a>Volet Schéma  
  
|**Pour**|**Appuyez sur**|**Cliquez sur**|  
|----------|-------------|-------------|  
|Vous déplacer entre des tables, des objets structurés en tables (et des lignes de jointures le cas échéant)|Tab ou Maj+Tab|Sur l'élément vers lequel vous voulez vous déplacer : table, objet structuré ou ligne de jointure|  
|Vous déplacer entre les colonnes d'une table ou d'un objet structuré en table|Touches de direction|Dans la colonne à laquelle vous voulez accéder|  
|Choisir la colonne de données sélectionnée pour la sortie|ESPACE ou touche PLUS|Sur la case à cocher en regard du nom de la colonne|  
|Supprimer la colonne de données sélectionnée du résultat de la requête|ESPACE ou touche MOINS|Sur la case à cocher en regard du nom de la colonne|  
|Supprimer la table, l'objet structuré en table ou la ligne de jointure de la requête|DELETE|Cliquez avec le bouton droit, puis cliquez sur **Supprimer**.|  
  
> [!NOTE]  
> Cette touche produit son effet sur tous les éléments sélectionnés. Pour sélectionner plusieurs éléments, appuyez sur la touche CTRL et, tout en la maintenant enfoncée, cliquez sur chaque élément.  
  
Pour plus d’informations, consultez [Volet Schéma &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md).  
  
## <a name="criteria-pane"></a>Volet Critères  
  
|Pour|Appuyez sur|Cliquez sur|  
|------|---------|---------|  
|Vous déplacer entre les cellules|Touches de direction, TAB ou MAJ+TAB|Sur la cellule cible|  
|Vous déplacer sur la dernière ligne d'une colonne sélectionnée|Ctrl+Flèche bas||  
|Vous déplacer sur la première ligne d'une colonne sélectionnée|Ctrl+Haut||  
|Vous déplacer sur la cellule située en haut à gauche dans la partie visible de la grille|CTRL+ORIGINE||  
|Vous déplacer sur la cellule située en bas à droite|CTRL+FIN||  
|Vous déplacer dans une liste déroulante|HAUT ou BAS|Sur le bouton dans la cellule|  
|Sélectionner une colonne entière dans la grille|Ctrl + Espace|Sur l'en-tête de la colonne|  
|Basculer entre le mode Édition et le mode de sélection des cellules|F2||  
|Copier le texte sélectionné dans la cellule à l'intérieur du Presse-papiers (en mode Édition)|CTRL+C||  
|Couper le texte sélectionné dans la cellule et le placer dans le Presse-papiers (en mode Édition)|Ctrl+X||  
|Coller le texte à partir du Presse-papiers (en mode Édition)|Ctrl+V||  
|Basculer entre les modes Insertion et Refrappe pendant la modification d'une cellule|INS||  
|Activer ou désactiver la case à cocher dans la colonne de sortie|ESPACE|Sur la case à cocher|  
|Effacer le contenu d'une cellule sélectionné|DELETE||  
|Effacer toutes les valeurs dans une colonne de grille sélectionnée|DELETE||  
|Insérer une ligne entre des lignes existantes|INS après avoir sélectionné une ligne dans la grille||  
|Ajouter une colonne Ou ...|INS après avoir sélectionné une colonne Ou ...||  
  
> [!NOTE]  
> Cette touche produit son effet sur tous les éléments sélectionnés.  
  
Pour plus d’informations, consultez [Volet Critères &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md).  
  
## <a name="sql-pane"></a>Volet SQL  
Quand vous travaillez dans le volet SQL, vous pouvez utiliser les touches d’édition Windows standard (par exemple, Ctrl+touches de direction pour vous déplacer entre les mots) et les commandes **Couper**, **Copier**et **Coller** du menu **Edition** .  
  
> [!NOTE]  
> Vous pouvez seulement insérer du texte : le mode Refrappe n'est pas disponible.  
  
Pour plus d’informations, consultez [Volet SQL &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="results-pane"></a>Volet Résultats  
  
|**Pour**|**Appuyez sur**|**Cliquez sur**|  
|----------|-------------|-------------|  
|Vous déplacer entre des cellules|Touches de direction, TAB ou MAJ+TAB|Sur la cellule cible|  
|Vous déplacer sur la première ou la dernière cellule de la ligne en cours|ORIGINE ou FIN||  
|Vous déplacer sur la première ligne de la colonne en cours|Ctrl+Haut||  
|Vous déplacer sur la cellule située en haut à gauche|CTRL+ORIGINE||  
|Vous déplacer sur la cellule du bas dans la première colonne|Ctrl+Flèche bas||  
|Étendre la sélection jusqu'au premier caractère d'une cellule|MAJ+ORIGNE||  
|Étendre la sélection jusqu'au dernier caractère d'une cellule|MAJ+FIN||  
|Basculer entre le mode Édition et le mode de sélection des cellules|F2||  
|Basculer entre les modes Insertion et Refrappe pendant la modification d'une cellule|INS||  
|Supprimer une ligne de la table|DELETE||  
|Annuler les modifications effectuées dans la cellule en cours|ÉCHAP dans une cellule qui a été modifiée||  
|Annuler les modifications effectuées dans la colonne en cours|ÉCHAP dans une cellule qui n'a pas été modifiée||  
|Entrer une valeur NULL dans une cellule|Ctrl+0||  
|Copier les colonnes ou les lignes sélectionnées dans le Presse-papiers|CTRL+C||  
|Copier le texte sélectionné dans la cellule à l'intérieur du Presse-papiers (en mode Édition)|CTRL+C||  
|Couper le texte sélectionné dans la cellule et le placer dans le Presse-papiers (en mode Édition)|Ctrl+X||  
|Coller le texte à partir du Presse-papiers (en mode Édition)|Ctrl+V||  
  
> [!NOTE]  
> Cette touche produit son effet sur tous les éléments sélectionnés.  
  
Pour plus d’informations, consultez [Volet Résultats &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
[Rubriques de procédures relatives à la conception de requêtes et de vues &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  

