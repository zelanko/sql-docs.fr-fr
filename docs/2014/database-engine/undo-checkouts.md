---
title: Annulation des extractions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 00662ef396ff114e4b77d70aa2f60863e8f94bd3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927842"
---
# <a name="undo-checkouts"></a>Annuler des extractions
  Vous pouvez utiliser la commande **Annuler l’extraction** pour annuler une extraction existante. Cette opération s'avère particulièrement utile lorsque vous avez modifié et enregistré un fichier et que vous devez par la suite annuler vos modifications.  
  
 En fonction des options que vous avez définies dans la boîte de dialogue **Annuler l’extraction options avancées** , l’environnement Studio conserve la copie de travail de l’élément sur votre disque local ou le remplace par la dernière version sous contrôle de code source. Si un utilisateur a modifié l'élément en dehors du contexte du système de contrôle de code source, la version extraite peut ne pas être la toute dernière.  
  
### <a name="to-undo-a-checkout"></a>Pour annuler une extraction  
  
1.  Dans l’Explorateur de solutions, sélectionnez le projet.  
  
2.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **Annuler l’extraction**.  
  
3.  Dans la boîte de dialogue **Annuler l’extraction** , sélectionnez les options appropriées, puis cliquez sur le bouton **Annuler l’extraction** .  
  
     **Colonnes**  
     Identifiez les colonnes à afficher et l'ordre dans lequel elles s'affichent.  
  
     **Affichage en 2D**  
     Permet d'afficher les éléments sous forme de liste en 2D sous leur connexion de contrôle de code source.  
  
     **Nom**  
     Indique les noms des éléments pour lesquels annuler l'extraction. Les cases à cocher en regard des éléments affichés sont activées. Si vous ne voulez pas annuler l'extraction d'un élément, désactivez sa case à cocher.  
  
     **Options**  
     Affiche les options d'annulation d'extraction spécifiques au plug-in de contrôle de code source lorsque vous cliquez sur la flèche à droite du bouton.  
  
     **Trier**  
     Permet d'ordonner les colonnes d'affichage.  
  
     **Arborescence**  
     Permet d'afficher la hiérarchie des dossiers et des éléments pour les éléments dont vous annulez l'extraction.  
  
     **Annuler l’extraction**  
     Permet d'annuler l'extraction, en supprimant toutes les modifications apportées au fichier extrait.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraire les fichiers](../../2014/database-engine/check-out-files.md)   
 [Gérer les extractions](../../2014/database-engine/manage-checkouts.md)  
  
  
