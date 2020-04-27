---
title: Général (boîte de dialogue restaurer la base de données) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.f1
ms.assetid: 319e7ef5-c9c7-4e50-8690-02a90aed006f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ebc1bc72a15545412adcc71d10feb08f3f05b16
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080944"
---
# <a name="general-restore-database-dialog-box-analysis-services---multidimensional-data"></a>Général (boîte de dialogue Restaurer la base de données) (Analysis Services - Données multidimensionnelles)
  La page **Général** de la boîte de dialogue **Restaurer la base de données** de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] permet de spécifier le fichier de sauvegarde et les paramètres généraux à utiliser lors de la restauration d'une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de restauration doit avoir l'autorisation de lire à partir de l'emplacement de sauvegarde spécifié pour chaque fichier. Pour restaurer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui n'est pas installée sur le serveur, l'utilisateur doit également être un membre du rôle serveur pour cette instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Pour remplacer une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , l’utilisateur doit avoir l’un des rôles suivants : membre du rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à restaurer.  
  
> [!NOTE]  
>  Après la restauration d'une base de données existante, l'utilisateur qui a restauré la base de données peut perdre l'accès à la base de données restaurée. Cette perte d'accès peut se produire si, au moment de la sauvegarde, l'utilisateur n'était pas un membre du rôle de serveur ou un membre du rôle de base de données avec les autorisations de contrôle total (Administrateur).  
  
 **Pour afficher la page Général dans la boîte de dialogue Restaurer la base de données**  
  
-   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur le dossier **Bases de données** d’une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou sur une base de données dans **l’Explorateur d’objets**, cliquez sur **Restaurer**puis, sous **Sélectionner une page**, cliquez sur **Général**.  
  
## <a name="options"></a>Options  
 **Script**  
 Crée un script de restauration basé sur les options sélectionnées dans la boîte de dialogue. Le script de restauration est écrit en langage de script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (ASSL).  
  
 Par défaut, lorsque vous cliquez sur l'icône **Script** , le script de restauration est envoyé dans une nouvelle fenêtre de requête.  
  
 Un menu s'affiche lorsque vous cliquez sur la flèche **Script** . Il vous permet de choisir où envoyer le script de restauration :  
  
-   Vers une nouvelle fenêtre de requête (par défaut).  
  
-   Vers un fichier.  
  
-   Vers le Presse-papiers.  
  
-   Vers un travail.  
  
 **Restaurer la base de données**  
 Sélectionnez la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à restaurer.  
  
 **À partir du fichier de sauvegarde**  
 Sélectionnez le fichier de sauvegarde à partir duquel restaurer la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] choisie.  
  
 **Parcourir**  
 Cliquez sur cette option pour afficher la boîte de dialogue **Rechercher les fichiers de base de données** et sélectionner le chemin et le nom du fichier de sauvegarde à utiliser. Pour plus d’informations sur la boîte de dialogue **Rechercher les fichiers de base de données**, consultez [Boîte de dialogue Rechercher les fichiers de base de données &#40;Analysis Services - Données multidimensionnelles&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Autoriser le remplacement de la base de données**  
 Sélectionnez cette option pour autoriser [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à restaurer le contenu du fichier de sauvegarde sélectionné sur les objets existants dans la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] choisie.  
  
 **Inclure des informations sur la sécurité**  
 Sélectionnez cette option pour copier les informations sur la sécurité stockées dans le fichier de sauvegarde vers la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 Lorsque cette option est sélectionnée, vous pouvez choisir la quantité d'informations sur la sécurité dans la liste déroulante activée par l'option. Les options suivantes sont disponibles :  
  
|Option|Description|  
|------------|-----------------|  
|**Copier tout**|Restaure les rôles de base de données contenus dans le fichier de sauvegarde, ainsi que les comptes d'utilisateurs associés aux rôles.|  
|**Ignorer l'appartenance**|Restaure les rôles de base de données contenus dans le fichier de sauvegarde, sans restaurer les comptes d'utilisateurs associés aux rôles.|  
  
 **Mot de passe**  
 Si le fichier de sauvegarde est chiffré, tapez le mot de passe utilisé lors de son chiffrement.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue restaurer la base de données &#40;Analysis Services-données multidimensionnelles&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Boîte de dialogue partitions &#40;boîte de dialogue restaurer la base de données&#41; &#40;Analysis Services-données multidimensionnelles&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
