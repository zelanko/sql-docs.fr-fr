---
title: Ajouter des tables à des schémas (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 26c13eb6c9cb142cac3ba0981177fb2c605ab5fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63297900"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a>Ajouter des tables à des schémas (Visual Database Tools)
  Vous pouvez ajouter une table à votre diagramme de base de données, afin de modifier sa structure ou de la mettre en relation avec d’autres tables du diagramme. Vous pouvez soit ajouter des tables de base de données existantes à un schéma, soit insérer une nouvelle table qui n'a pas encore été définie dans la base de données.  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a>Pour insérer une nouvelle table dans un schéma  
  
1.  Vérifiez que vous êtes connecté à la base de données dans laquelle vous voulez créer la table.  
  
     Pour créer une table dans votre schéma actuel, cliquez sur le bouton **Nouvelle table** dans la barre d'outils.  
  
     -ou-  
  
     Cliquez avec le bouton droit dans le schéma et, dans le menu contextuel, cliquez sur **Nouvelle table**.  
  
2.  Dans la boîte de dialogue **Choisir un nom** , modifiez ou acceptez le nom de table assigné par le système, puis cliquez sur **OK**.  
  
     Une nouvelle table apparaît dans le schéma en mode d'affichage Standard.  
  
3.  Dans la première cellule de la nouvelle table, tapez un nom de colonne. Ensuite, appuyez sur la touche TAB pour passer à la cellule suivante.  
  
4.  Sous **Type de données**, sélectionnez un type de données pour la colonne. Chaque colonne doit avoir un nom et un type de données.  
  
     Vous pouvez définir les autres propriétés des colonnes dans le Concepteur de tables.  
  
5.  Répétez les étapes 3 et 4 pour chaque colonne que vous souhaitez ajouter à la table.  
  
> [!NOTE]  
>  Lorsque vous enregistrez votre diagramme de base de données, la nouvelle table est ajoutée à votre base de données.  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a>Pour ajouter une table existante à un schéma  
  
1.  Vérifiez que vous êtes connecté à la base de données dont vous voulez modifier des tables.  
  
2.  Sélectionnez une table dans le dossier **Tables** .  
  
3.  Faites glisser la table jusqu’à votre diagramme de base de données.  
  
4.  Relâchez le bouton de la souris.  
  
> [!NOTE]  
>  S'il existe des relations entre la table sélectionnée et d'autres tables de votre schéma, les lignes de relation correspondantes sont dessinées automatiquement.  
  
### <a name="to-add-related-tables-to-a-diagram"></a>Pour ajouter des tables connexes à un schéma  
  
1.  Sélectionnez une ou plusieurs tables associées à des contraintes de clé étrangère dans le diagramme de base de données.  
  
2.  Cliquez avec le bouton droit sur l’une des tables sélectionnées et, dans le menu contextuel, cliquez sur **Ajouter les tables connexes**.  
  
> [!NOTE]  
>  Toutes les tables référencées par une contrainte de clé étrangère depuis les tables sélectionnées et toutes les tables qui référencent les tables sélectionnées avec une contrainte de clé étrangère sont ajoutées au schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des schémas de base de données &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Utiliser des tables dans les diagrammes de base de données &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
