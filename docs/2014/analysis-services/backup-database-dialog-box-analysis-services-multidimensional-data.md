---
title: Boîte de dialogue sauvegarder la base de données (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Backup.f1
ms.assetid: 7811ce7d-6c37-4189-bfa6-ef36fb4932db
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96ddf88bd6f071c667a021678b6f5cd2613ae8db
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527825"
---
# <a name="backup-database-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Sauvegarder la base de données (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Sauvegarder la base de données** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour sauvegarder une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans un fichier de sauvegarde en utilisant le format de fichier de sauvegarde .abf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Pour chaque fichier de sauvegarde, l'utilisateur qui exécute la commande de sauvegarde doit avoir l'autorisation d'écrire dans l'emplacement de sauvegarde spécifié pour chaque fichier. L’utilisateur doit aussi avoir l’un des rôles suivants : membre d’un rôle serveur pour l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou membre d’un rôle de base de données avec les autorisations de contrôle total (Administrateur) sur la base de données à sauvegarder.  
  
 **Pour afficher la boîte de dialogue Sauvegarder la base de données**  
  
-   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur le dossier **Bases de données** d’une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou sur une base de données dans **l’Explorateur d’objets**, puis cliquez sur **Sauvegarder**.  
  
## <a name="options"></a>Options  
 **Script**  
 Crée un script de sauvegarde basé sur les options sélectionnées dans la boîte de dialogue. Le script de restauration est écrit en langage de script [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (ASSL).  
  
 Par défaut, lorsque vous cliquez sur l'icône **Script** , le script de sauvegarde est envoyé dans une nouvelle fenêtre de requête.  
  
 Un menu s'affiche lorsque vous cliquez sur la flèche **Script** . Il vous permet de choisir où envoyer le script de sauvegarde :  
  
-   Vers une nouvelle fenêtre de requête (par défaut).  
  
-   Vers un fichier.  
  
-   Vers le Presse-papiers.  
  
-   Vers un travail.  
  
 **Sauvegarde de la base de données**  
 Affiche le nom de la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sélectionnée.  
  
 **Fichier de sauvegarde**  
 Tapez le chemin d'accès complet et le nom du fichier de sauvegarde à utiliser.  
  
 **Parcourir**  
 Cliquez pour afficher la boîte de dialogue **Enregistrer le fichier sous** et sélectionnez le chemin et le nom du fichier de sauvegarde à utiliser. Pour plus d’informations sur la boîte de dialogue **Enregistrer le fichier sous**, consultez [Boîte de dialogue Enregistrer le fichier sous &#40;Analysis Services - Données multidimensionnelles&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Autoriser le remplacement du fichier**  
 Sélectionnez cette option pour remplacer un fichier de sauvegarde existant ou un fichier de sauvegarde distant, s'il en existe un.  
  
> [!NOTE]  
>  Si cette option n'est pas sélectionnée et que le fichier de sauvegarde défini dans **Fichier de sauvegarde** ou un fichier de sauvegarde distant défini dans **Fichier de sauvegarde distant** existe, une erreur se produit.  
  
 **Appliquer la compression**  
 Sélectionnez cette option pour compresser le contenu du fichier de sauvegarde et, si définis, les fichiers de sauvegarde distants.  
  
 **Chiffrer le fichier de sauvegarde**  
 Sélectionnez cette option pour chiffrer le fichier de sauvegarde en utilisant le mot de passe défini dans **Mot de passe**.  
  
 **Mot de passe**  
 Tapez le mot de passe à utiliser lors du chiffrement du fichier de sauvegarde, et si définis, des fichiers de sauvegarde distants.  
  
> [!NOTE]  
>   Cette option est activée uniquement si **Chiffrer le fichier de sauvegarde** est sélectionné.  
  
 **Confirmer le mot de passe**  
 Tapez le mot de passe entré dans **Mot de passe** pour confirmer le mot de passe du fichier de sauvegarde et, s’ils sont spécifiés, des fichiers de sauvegarde distants.  
  
> [!NOTE]  
>   Cette option est activée uniquement si **Chiffrer le fichier de sauvegarde** est sélectionné.  
  
 **Partitions distantes de la sauvegarde**  
 Sélectionnez cette option pour inclure les informations d'emplacement et les données des partitions distantes dans le fichier de sauvegarde.  
  
> [!NOTE]  
>  Cette option est activée uniquement si la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sélectionnée utilise des partitions distantes.  
  
 **Emplacement de la sauvegarde de la partition distante**  
 Affiche l'emplacement des partitions distantes associées à la base de données sélectionnée, ainsi que le fichier de sauvegarde distant utilisé pour sauvegarder les données et les métadonnées des partions distantes. Les colonnes suivantes sont disponibles :  
  
|Colonne|Description|  
|------------|-----------------|  
|**Serveur**|Affiche l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère les partitions distantes.|  
|**Sauvegarde de la base de données**|Affiche la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui contient les partitions distantes.|  
|**Liste des partitions**|Affiche la liste des partitions distantes contenues dans la base de données affichée dans **Base de données**.|  
|**Fichier de sauvegarde distant**|Tapez le chemin complet et le nom du fichier de sauvegarde distant à utiliser, ou cliquez sur le bouton représentant des points de suspension (**...**) pour afficher la boîte de dialogue **Enregistrer le fichier sous** et sélectionner le chemin et le nom du fichier de sauvegarde distant à utiliser. Pour plus d’informations sur la boîte de dialogue **Enregistrer le fichier sous**, consultez [Boîte de dialogue Enregistrer le fichier sous &#40;Analysis Services - Données multidimensionnelles&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Sauvegarde et restauration de bases de données Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
