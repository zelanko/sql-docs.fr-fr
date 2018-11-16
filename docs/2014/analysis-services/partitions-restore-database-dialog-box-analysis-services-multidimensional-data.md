---
title: Partitions (boîte de dialogue Restauration de base de données) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ef5ec59980d267a8ead0f69aedb12c6eca5508dc
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51639866"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a>Partitions (boîte de dialogue Restaurer la base de données) (Analysis Services - Données multidimensionnelles)
  Utilisez la page **Partitions** de la boîte de dialogue **Restaurer la base de données** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] afin de spécifier l’emplacement de restauration des partitions locales et les fichiers de sauvegarde à distance à utiliser lors de la restauration des partitions distantes, et pour indiquer si les partitions distantes doivent, ou non, être restaurées.  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance d’ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
> [!NOTE]  
>  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
 **Pour afficher la page Partitions dans la boîte de dialogue Restaurer la base de données**  
  
-   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit soit sur le dossier **Bases de données** d’une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou sur une base de données dans **l’Explorateur d’objets**, cliquez sur **Restaurer**, puis sous **Sélectionner une page**, cliquez sur **Partitions**.  
  
## <a name="options"></a>Options  
 **Script**  
 Crée un script de restauration basé sur les options sélectionnées dans la boîte de dialogue. Le script de restauration est écrit en langage de script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (ASSL).  
  
 Par défaut, lorsque vous cliquez sur l'icône **Script** , le script de restauration est envoyé dans une nouvelle fenêtre de requête.  
  
 Un menu s'affiche lorsque vous cliquez sur la flèche **Script** . Il vous permet de choisir où envoyer le script de restauration :  
  
-   Vers une nouvelle fenêtre de requête (par défaut).  
  
-   Vers un fichier.  
  
-   Vers le Presse-papiers.  
  
-   Vers un travail.  
  
 **Restaurer vers des emplacements d’origine**  
 Sélectionnez cette option afin de restaurer les partitions locales contenues dans le fichier de sauvegarde vers leurs emplacements d'origine.  
  
 **Sélectionnez différents emplacements**  
 Choisissez cette option pour indiquer les différents emplacements vers lesquels les partitions locales seront restaurées.  
  
> [!NOTE]  
>  Vous pouvez uniquement modifier le dossier de restauration d'une partition locale si l'emplacement spécifié pour cette partition dans le cube n'était pas celui par défaut.  
  
 La grille suivante, active lorsque cette option est sélectionnée, permet de spécifier un dossier de restauration pour chaque partition locale :  
  
|colonne|Description|  
|------------|-----------------|  
|**Cube**|Affiche le nom du cube qui contient la partition locale.|  
|**Groupe de mesures**|Affiche le nom du groupe de mesures qui contient la partition locale.|  
|**Partition**|Affiche le nom de la partition locale.|  
|**Taille (Mo)**|Affiche la taille (en mégaoctets) de la partition locale.|  
|**Dossier d’origine**|Affiche le nom du dossier original dans lequel la partition locale était stockée.|  
|**Dossier de restauration**|Tapez le nom du dossier de restauration de la partition locale ou cliquez sur le bouton de sélection (**...**) pour afficher la boîte de dialogue **Rechercher un dossier distant** et sélectionner le chemin du dossier à utiliser. Pour plus d'informations sur la boîte de dialogue **Rechercher un dossier distant**, consultez [Boîte de dialogue Rechercher un dossier distant &#40;Analysis Services - Données multidimensionnelles&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).|  
  
 **Restaurer les partitions distantes**  
 Sélectionnez cette option pour restaurer les partitions distantes stockées dans les fichiers de sauvegarde à distance.  
  
> [!NOTE]  
>  Cette option est uniquement active si le fichier de sauvegarde contient des références à des partitions distantes.  
  
 La grille suivante, active lorsque cette option est sélectionnée, permet de spécifier un dossier de restauration pour chaque partition locale :  
  
|colonne|Description|  
|------------|-----------------|  
|**Server**|Affiche le nom de l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère la partition distante.|  
|**Source de données**|Affiche le nom de la source de données dans le fichier de sauvegarde qui correspond à la base de données contenant la partition distante.|  
|**Fichier de sauvegarde**|Tapez le chemin complet et le nom du fichier de sauvegarde à distance à utiliser ou cliquez sur le bouton de sélection (**...**) pour afficher la boîte de dialogue **Rechercher les fichiers de base de données** et sélectionner le chemin et le nom du fichier en question. Pour plus d’informations sur la boîte de dialogue **Rechercher les fichiers de base de données**, consultez [Boîte de dialogue Rechercher les fichiers de base de données &#40;Analysis Services - Données multidimensionnelles&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).|  
|**...**|Cliquez sur ce bouton pour afficher la boîte de dialogue **Partitions distantes - Paramètres avancés** et modifier les options avancées liées à la restauration de la partition distante, telles que la chaîne de connexion de la source de données. Pour plus d’informations sur la boîte de dialogue **Partitions distantes - Paramètres avancés**, consultez [Boîte de dialogue Partitions distantes - Paramètres avancés &#40;Analysis Services - Données multidimensionnelles&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Restaurer la base de données &#40;Analysis Services - Données multidimensionnelles&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Général &#40;restaurer la boîte de dialogue base de données&#41; &#40;Analysis Services - données multidimensionnelles&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
