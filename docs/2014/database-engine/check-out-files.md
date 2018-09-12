---
title: Extraire les fichiers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 313d5d85bd7ad8343fe90f0eeda16bf15e53ef44
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808435"
---
# <a name="check-out-files"></a>Extraire des fichiers
  À moins que [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ne soit configuré pour autoriser la modification des fichiers archivés, vous devez extraire un fichier avant de pouvoir le modifier. Lorsque vous procédez à l'extraction d'un fichier, une version du fichier est copiée sur votre disque local et l'attribut de lecture seule du fichier est désactivé.  
  
 Vous pouvez extraire des fichiers en mode exclusif ou en mode partagé. Lorsque vous procédez à l'extraction d'un fichier de manière exclusive, aucun autre utilisateur ne peut l'extraire tant que vous ne l'avez pas archivé. Lorsque vous procédez à l'extraction d'un fichier en mode partagé, d'autres utilisateurs peuvent l'extraire et le modifier ; lorsque vous l'archivez, vous pouvez être amené à fusionner la version que vous avez extraite avec les versions créées par d'autres utilisateurs.  
  
 Utilisez le **Check Out** commande pour extraire les fichiers et les projets sous contrôle de code source. Lorsque vous utilisez cette commande pour extraire une solution ou un projet, tous les fichiers figurant dans cette solution ou dans ce projet sont également extraits. Lorsque vous extrayez un fichier de code source individuel, cela n'entraîne toutefois pas l'extraction du projet ou de la solution dont il fait partie.  
  
> [!NOTE]  
>  Si le [!INCLUDE[msCoName](../includes/msconame-md.md)] base de données Visual SourceSafe pour votre projet est configuré pour autoriser les extractions multiples, et que vous souhaitez extraire un fichier exclusivement, vous devez effacer le **autoriser les extractions multiples** option dans le  **Advanced Options d’extraction** boîte de dialogue avant d’extraire le fichier. Vous devez redémarrer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour que ce paramètre soit pris en compte.  
  
### <a name="to-check-out-a-file"></a>Pour extraire un fichier  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet ou le fichier.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **extraire pour modification**.  
  
3.  Si le **extraire pour modification** boîte de dialogue s’affiche, sélectionnez les éléments de votre choix, cliquez sur **Check Out**. Si vous avez configuré le [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environnement ne pas pour afficher le **Check Out** boîte de dialogue, les éléments sélectionnés dans l’Explorateur de solutions et toutes leurs enfants potentiels sont immédiatement extraits.  
  
     **Vérifier**  
     Extrait tous les éléments sélectionnés.  
  
     **Colonnes**  
     Identifiez les colonnes à afficher et l'ordre dans lequel elles s'affichent.  
  
     **Commentaires**  
     Ajoutez un commentaire à associer à l'opération d'extraction.  
  
     **Ne pas afficher boîte de dialogue lors de l’extraction d’éléments**  
     La boîte de dialogue n'est pas affichée au cours des opérations d'extraction.  
  
     **Affichage en 2D**  
     Affiche les éléments que vous extrayez sous forme de liste en 2D sous leur connexion de contrôle de code source.  
  
     **Modifier**  
     Permet de modifier un élément sans l'extraire. Le **modifier** bouton s’affiche uniquement si vous avez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] configuré pour prendre en charge la modification des fichiers archivés.  
  
     **Nom**  
     Affiche les noms des éléments disponibles en vue d'une extraction. Les cases à cocher activées indiquent les éléments sélectionnés. Si vous ne souhaitez pas extraire un élément donné, désactivez la case à cocher correspondante.  
  
     **Options**  
     Affiche les options d'extraction spécifiques du plug-in de contrôle de code source quand vous cliquez sur la flèche à droite du bouton.  
  
     **Sort**  
     Trie les colonnes affichées.  
  
     **Vue d’arborescence**  
     Affiche la hiérarchie de dossiers et de fichiers pour l'élément que vous extrayez.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des fichiers archivés](../../2014/database-engine/edit-checked-in-files.md)   
 [Extraire automatiquement des fichiers lors de leur modification](../../2014/database-engine/automatically-check-out-files-upon-edit.md)   
 [Annuler des extractions](../../2014/database-engine/undo-checkouts.md)   
 [Gérer les extractions](../../2014/database-engine/manage-checkouts.md)  
  
  
