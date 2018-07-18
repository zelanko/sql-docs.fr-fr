---
title: Ajouter une référence, boîte de dialogue (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.addreference.f1
- sql12.asvs.bidevstudio.assembly.addassembly.f1
helpviewer_keywords:
- Add Reference dialog box
ms.assetid: 457958c4-6baa-474d-99a0-34c195ceba09
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0593f8a598894bbe08fb4657c980b208d8f29a64
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244066"
---
# <a name="add-reference-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Ajouter une référence (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Ajouter une référence** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour ajouter une référence à un assembly [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework ou à un autre projet à votre projet de développement. Vous pouvez afficher la boîte de dialogue **Ajouter une référence** en cliquant avec le bouton droit de la souris sur le dossier **Assemblys** du projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans **l’Explorateur de solutions** et en sélectionnant **Nouvelle référence de l’assembly** dans le menu contextuel.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**.NET**|Sélectionnez cet onglet pour ajouter une référence à un composant enregistré. Cet onglet affiche une grille qui contient une liste de composants .NET Framework enregistrés. Sélectionnez un ou plusieurs éléments de la grille et cliquez sur **Ajouter** pour ajouter les composants sélectionnés .NET à **Produits et composants sélectionnés**. Cette grille comporte les colonnes suivantes :<br /><br /> **Nom du composant**: nom complet ou « convivial » du composant. Sélectionnez le titre pour trier les composants en fonction de leur nom.<br /><br /> **Version**: le numéro de version répertorié du composant. Sélectionnez le titre pour trier les composants en fonction de leur version.<br /><br /> **Runtime**: la version du .NET Framework sur laquelle repose le composant. Sélectionnez le titre pour trier en fonction de la version d'exécution.<br /><br /> **Chemin d’accès**: le nom de fichier du composant et le chemin d’accès où il se trouve. Sélectionnez le titre pour trier les composants en fonction de leur chemin d'accès.|  
|**Parcourir**|Cliquez pour rechercher dans le système de fichiers un assembly ne figurant pas dans l'onglet **.NET** ou **Récent** . Cet onglet contient les options suivantes :<br /><br /> **Regarder dans**: sélectionnez un dossier dans cette liste déroulante. Si vous sélectionnez un dossier dans cette liste, son contenu s'affiche dans le volet principal.<br /><br /> **Atteindre le dernier dossier visité**: retourne **Regarder dans** à l’emplacement précédent.<br /><br /> **Dossier parent**: localise le dossier le plus élevé dans la hiérarchie.<br /><br /> **Créer un nouveau dossier**: sélectionnez cette option pour créer un dossier enfant sous le dossier sélectionné dans **Regarder dans**.<br /><br /> **Afficher le Menu**: sélectionnez cette option pour modifier l’affichage du contenu dans le volet principal.  Pour plus d'informations sur les options du **menu Afficher**, consultez la rubrique « Présentation de l'affichage des fichiers et des dossiers » de la documentation [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. Les options suivantes sont disponibles :<br />Miniatures<br />Mosaïques<br />Icônes<br />Liste<br />Détails<br /><br /> **Volet principal**: affiche le contenu du dossier sélectionné dans **Regarder dans**. Sélectionnez un ou plusieurs éléments, puis cliquez sur **ajouter** pour ajouter les fichiers sélectionnés à **produits et composants sélectionnés**. Pour plus d'informations sur les options et le menu contextuel du volet principal, consultez la rubrique « Présentation de l'affichage des fichiers et des dossiers » de la documentation Windows.<br /><br /> **Nom de fichier**: utilisez cette option pour filtrer les fichiers et dossiers qui sont affichés. Tapez un nom de fichier complet ou partiel sur lequel filtrer. Vous pouvez utiliser l'astérisque (\*) comme caractère générique. Tapez plusieurs noms de fichiers (chaque nom de fichier entre guillemets doubles (") et délimité par un espace) pour sélectionner plusieurs fichiers. Vous pouvez également sélectionner des fichiers déjà affichés en sélectionnant leur nom dans la liste déroulante. Conseil : Vous pouvez localiser les serveurs Web et les ordinateurs du réseau en entrant un URL ou un chemin réseau dans **nom de fichier**. Par exemple, « http://mywebsite » affiche les fichiers disponibles à l’emplacement « monsiteweb », tandis que «\\\monserveur\partage » affiche les fichiers disponibles à l’emplacement « partage » sur « monserveur ».<br /><br /> **Types de fichiers**: utilisez cette option pour filtrer le contenu du dossier ou du répertoire sélectionné dans **Regarder dans** pour un type de fichier particulier.|  
|**Récents**|Affiche la liste des références de composants qui viennent d'être ajoutées au projet dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Sélectionnez un ou plusieurs éléments de la grille et cliquez sur **Ajouter** pour ajouter les assemblys .NET Framework sélectionnés à **Produits et composants sélectionnés**. Cette grille comporte les colonnes suivantes :<br /><br /> **Nom du composant**: nom complet ou « convivial » du composant. Sélectionnez le titre pour trier les composants en fonction de leur nom.<br /><br /> **Version**: le numéro de version répertorié du composant. Sélectionnez le titre pour trier les composants en fonction de leur version.<br /><br /> **Runtime**: la version du .NET Framework sur laquelle repose le composant. Sélectionnez le titre pour trier en fonction de la version d'exécution.<br /><br /> **Chemin d’accès**: le nom de fichier du composant et le chemin d’accès où il se trouve. Sélectionnez le titre pour trier les composants en fonction de leur chemin d'accès.|  
|**Ajouter**|Cliquez pour ajouter un composant sélectionné dans les onglets **.NET**, **Parcourir**ou **Récent** à **Projets et composants sélectionnés**.|  
|**Supprimer**|Cliquez pour supprimer un composant sélectionné dans **Projets et composants sélectionnés**.|  
|**Projets et composants sélectionnés**|Affiche la liste des références de composants à ajouter au projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Sélectionnez un ou plusieurs éléments dans la grille et cliquez sur **Supprimer** pour supprimer les composants sélectionnés de la grille. Cette grille comporte les colonnes suivantes :<br /><br /> **Nom du composant**: nom complet ou « convivial » du composant. Sélectionnez le titre pour trier les composants en fonction de leur nom.<br /><br /> **Version**: le numéro de version répertorié du composant. Sélectionnez le titre pour trier les composants en fonction de leur version.<br /><br /> **Runtime**: la version du .NET Framework sur laquelle repose le composant. Sélectionnez le titre pour trier en fonction de la version d'exécution.<br /><br /> **Chemin d’accès**: le nom de fichier du composant et le chemin d’accès où il se trouve. Sélectionnez le titre pour trier les composants en fonction de leur chemin d'accès.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Gestion des assemblys de modèle multidimensionnel](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
