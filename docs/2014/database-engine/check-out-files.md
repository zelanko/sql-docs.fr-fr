---
title: Extraire les fichiers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 10c076f7bee35e0e466fc22aec9ad9f6984bac6a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936030"
---
# <a name="check-out-files"></a>Extraire des fichiers
  À moins que [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ne soit configuré pour autoriser la modification des fichiers archivés, vous devez extraire un fichier avant de pouvoir le modifier. Lorsque vous procédez à l'extraction d'un fichier, une version du fichier est copiée sur votre disque local et l'attribut de lecture seule du fichier est désactivé.  
  
 Vous pouvez extraire des fichiers en mode exclusif ou en mode partagé. Lorsque vous procédez à l'extraction d'un fichier de manière exclusive, aucun autre utilisateur ne peut l'extraire tant que vous ne l'avez pas archivé. Lorsque vous procédez à l'extraction d'un fichier en mode partagé, d'autres utilisateurs peuvent l'extraire et le modifier ; lorsque vous l'archivez, vous pouvez être amené à fusionner la version que vous avez extraite avec les versions créées par d'autres utilisateurs.  
  
 Utilisez la commande **extraire** pour extraire des projets et des fichiers sous contrôle de code source. Si vous utilisez cette commande pour extraire une solution ou un projet, tous les fichiers de la solution ou du projet sont également extraits. Toutefois, l’extraction d’un fichier de code source individuel n’entraîne pas l’extraction du projet ou de la solution auxquels il appartient.  
  
> [!NOTE]  
>  Si la [!INCLUDE[msCoName](../includes/msconame-md.md)] base de données Visual SourceSafe pour votre projet est configurée pour autoriser plusieurs extractions et que vous souhaitez extraire un fichier en mode exclusif, vous devez désactiver l’option **autoriser plusieurs extractions** dans la boîte de dialogue Options d’extraction **avancées** avant d’extraire le fichier. Vous devez redémarrer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour que ce paramètre soit pris en compte.  
  
### <a name="to-check-out-a-file"></a>Pour extraire un fichier  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet ou le fichier.  
  
2.  Dans le menu **fichier** , pointez sur **contrôle de code source**, puis cliquez sur **Extraire pour modification**.  
  
3.  Si la boîte **de dialogue Extraire pour modification** s’affiche, sélectionnez les éléments souhaités, puis cliquez sur **extraire**. Si vous avez configuré l' [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environnement pour qu’il n’affiche pas la boîte de dialogue **extraire** , les éléments sélectionnés dans Explorateur de solutions et tous les enfants qu’ils peuvent avoir sont immédiatement extraits.  
  
     **Vérifier**  
     Extrait tous les éléments sélectionnés.  
  
     **Colonnes**  
     Identifiez les colonnes à afficher et l'ordre dans lequel elles s'affichent.  
  
     **Commentaires**  
     Ajoutez un commentaire à associer à l'opération d'extraction.  
  
     **Ne pas afficher la boîte de dialogue Extraire lors de l'extraction d'éléments**  
     La boîte de dialogue n'est pas affichée au cours des opérations d'extraction.  
  
     **Affichage en 2D**  
     Affiche les éléments que vous extrayez sous forme de liste en 2D sous leur connexion de contrôle de code source.  
  
     **Modifier**  
     Modifiez un élément sans l’extraire. Le bouton **modifier** s’affiche uniquement si vous avez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] configuré pour prendre en charge la modification des fichiers archivés.  
  
     **Nom**  
     Affiche les noms des éléments disponibles en vue d'une extraction. Les cases à cocher activées indiquent les éléments sélectionnés. Si vous ne souhaitez pas extraire un élément donné, désactivez la case à cocher correspondante.  
  
     **Options**  
     Affiche les options d'extraction spécifiques du plug-in de contrôle de code source quand vous cliquez sur la flèche à droite du bouton.  
  
     **Trier**  
     Trie les colonnes affichées.  
  
     **Arborescence**  
     Affiche la hiérarchie de dossiers et de fichiers pour l'élément que vous extrayez.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier les fichiers archivés](../../2014/database-engine/edit-checked-in-files.md)   
 [Extraire automatiquement des fichiers lors de la modification](../../2014/database-engine/automatically-check-out-files-upon-edit.md)   
 [Annulation des extractions](../../2014/database-engine/undo-checkouts.md)   
 [Gérer les extractions](../../2014/database-engine/manage-checkouts.md)  
  
  
