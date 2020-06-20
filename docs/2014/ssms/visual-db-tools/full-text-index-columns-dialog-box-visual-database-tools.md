---
title: Colonnes d’index de texte intégral, boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: d4d77bb77ab3cf0fecc2e254af53782f982923ae
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054585"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a>Boîte de dialogue Colonnes d'index de texte intégral (Visual Database Tools)
  Cette boîte de dialogue répertorie les colonnes qui participent à l'index de texte intégral pour la table ouverte dans le Concepteur de tables. Pour accéder à cette boîte de dialogue, cliquez avec le bouton droit sur la table dans le Concepteur de tables, choisissez **Index de texte intégral**, et dans la boîte de dialogue **Index de texte intégral**, cliquez sur l’index avec les colonnes que vous souhaitez afficher ou modifier, cliquez sur le champ **Colonnes** dans la grille à droite et enfin, cliquez sur le bouton de sélection ( **...** ).  
  
## <a name="options"></a>Options  
 **Colonne**  
 Affiche le nom des colonnes qui participent à l'index de texte intégral. Pour ajouter une colonne, cliquez dans la première cellule vide et choisissez une colonne dans la liste déroulante. Seules les colonnes avec le type de données texte ou image sont accessibles.  
  
 **Type de données**  
 Affiche le type de données pour chaque colonne. Il s’agit d’une propriété en lecture seule. Pour modifier un type de données, ouvrez la table dans le Concepteur de tables, cliquez sur la colonne et modifiez le type de données sous l’onglet **Propriétés des colonnes** .  
  
 **Saisi par colonne**  
 S'applique uniquement aux colonnes avec le type de données `image`. Fournit une liste déroulante dans laquelle vous pouvez choisir les autres colonnes qui représentent le type de données de cette colonne. Si cette colonne n'a pas de type de données `image`, la valeur sera équivalente à Aucun.  
  
 Les colonnes avec le type de données `image` peuvent contenir des fichiers Microsoft Office™ (.doc, .xls et .ppt), des fichiers texte (.txt) et des fichiers HTML (.htm), et l'affectation de la valeur d'image au type de données de cette colonne permet à la recherche en texte intégral de rechercher le contenu des fichiers.  
  
 **Langage**  
 Répertorie les langues disponibles. Dans la liste déroulante, choisissez la langue appropriée pour les données de la colonne. Par exemple, si vous utilisez un système d'exploitation en français, mais souhaitez indexer une colonne qui contient de l'allemand, choisissez Allemand dans la liste déroulante pour obtenir un index plus performant.  
  
 **Sémantique statistique**  
 Sélectionnez s'il faut activer l'indexation sémantique pour la colonne sélectionnée. Pour plus d’informations, consultez [Recherche sémantique &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).  
  
 Si vous sélectionnez une **langue** avant de sélectionner **Sémantique statistique**, et que la langue sélectionnée n'est pas associée à un modèle linguistique sémantique, la case à cocher **Sémantique statistique** est désactivée. Si vous sélectionnez **Sémantique statistique** avant de sélectionner une **langue**, les langues disponibles dans la zone de liste déroulante sont limitées à celles pour lesquelles il existe une prise en charge de modèle linguistique sémantique.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Index de texte intégral &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
