---
title: Boîte de dialogue partitions distantes-paramètres avancés (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.advancedrestoresettings.f1
ms.assetid: a03bb7e1-efaf-47c8-b0ee-f3e4438311cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ca3f12ff53c4291d8bbe7c8eb97ce8e47172ea3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070380"
---
# <a name="remote-partitions---advanced-settings-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Partitions distantes - Paramètres avancés (Analysis Services - Données multidimensionnelles)
  La boîte de dialogue **Partitions distantes - Paramètres avancés** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] permet de modifier les paramètres avancés tels que la chaîne de connexion à la source de données représentant la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante qui englobe les partitions distantes, tout en restaurant ces partitions distantes à partir d’un fichier de sauvegarde distant vers une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans la boîte de dialogue **Restaurer la base de données** . Pour accéder à cette boîte de dialogue, sélectionnez l’option **Restaurer les partitions distantes** puis cliquez sur le bouton, représenté par les points de suspension ( **...** ), correspondant à une partition distante. Dans la boîte de dialogue **Restaurer la base de données** , ouvrez la page**Partitions**où vous retrouverez ainsi la boîte de dialogue **Partitions distantes - Paramètres avancés** .  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom de la source de données**|Affiche le nom de la source de données représentant la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante chargée de gérer les partitions distantes répertoriées.|  
|**Fichier de sauvegarde**|Affiche le nom du fichier de sauvegarde qui contient les données à restaurer concernant les partitions distantes répertoriées.<br /><br /> Remarque : aucun fichier de sauvegarde n’est affiché si un fichier de sauvegarde distant a été spécifié dans la colonne **fichier de sauvegarde** de la page **partitions** de la boîte de dialogue **restaurer la base de données** .|  
|**Chaîne de connexion**|Affiche la chaîne de connexion pour la source de données apparaissant dans **Nom de la source de données**.|  
|**Modifier**|Permet d'afficher la boîte de dialogue **Propriétés des liaisons de données** et de modifier les propriétés contenues dans la chaîne de connexion.|  
|**Liste des partitions**|Permet d'indiquer différents emplacements dans lesquels doivent être restaurées les partitions distantes. Notez que vous pouvez uniquement modifier le dossier de restauration d’une partition distante si l’emplacement spécifié pour cette partition distante dans le cube n’était pas celui par défaut. La grille suivante, activée si l'option est cochée, permet d'indiquer un dossier de restauration pour chaque partition distante :<br /><br /> **Cube**: affiche le nom du cube qui contient la partition distante.<br /><br /> **MeasureGroup**: affiche le nom du groupe de mesures qui contient la partition distante.<br /><br /> **Partition**: affiche le nom de la partition distante.<br /><br /> **Taille (Mo)**: affiche la taille, en mégaoctets, de la partition distante.<br /><br /> **Dossier d’origine**: affiche le nom du dossier d’origine dans lequel la partition distante a été stockée.<br /><br /> **Dossier de restauration**: tapez le nom du dossier de restauration de la partition distante, ou cliquez sur le bouton de sélection (**...**) pour afficher la boîte de dialogue **Rechercher un dossier distant** et sélectionner le chemin d’accès du dossier à utiliser. Pour plus d'informations sur la boîte de dialogue **Rechercher un dossier distant**, consultez [Boîte de dialogue Rechercher un dossier distant &#40;Analysis Services - Données multidimensionnelles&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Boîte de dialogue partitions &#40;boîte de dialogue restaurer la base de données&#41; &#40;Analysis Services-données multidimensionnelles&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
