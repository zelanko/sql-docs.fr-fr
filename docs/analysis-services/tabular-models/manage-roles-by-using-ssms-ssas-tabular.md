---
title: Gérer les rôles de modèles tabulaires Analysis Services à l’aide de SSMS | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 22fd8242de50f73eee634d1bc6bc3fcf5e887f0b
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072616"
---
# <a name="manage-roles-by-using-ssms"></a>Gérer les rôles à l'aide de SSMS 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Vous pouvez créer, modifier et gérer les rôles pour un modèle tabulaire déployé à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Tâches de cette rubrique :  
  
-   [Pour créer un rôle](#bkmk_new_role)  
  
-   [Pour copier un rôle](#bkmk_copy_role)  
  
-   [Pour modifier un rôle](#bkmk_edit_role)  
  
-   [Pour supprimer un rôle](#bkmk_deletet_role)  
  
> [!CAUTION]  
>  Le redéploiement d'un projet de modèle tabulaire avec les rôles définis à l'aide du Gestionnaire de rôles de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] remplace les rôles définis dans un modèle tabulaire déployé.  
  
> [!CAUTION]  
>  L'utilisation de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour gérer une base de données d'espace de travail model tabulaire alors que le projet de modèle est ouvert dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] peut entraîner l'altération du fichier Model.bim. Lors de la création et de la gestion des rôles pour une base de données d'espace de travail model tabulaire, utilisez le Gestionnaire de rôles de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
###  <a name="bkmk_new_role"></a> Pour créer un rôle  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez la base de données model tabulaire pour laquelle vous voulez créer un rôle, cliquez avec le bouton droit sur **Rôles**, puis cliquez sur **Nouveau rôle**.  
  
2.  Dans la boîte de dialogue **Créer un rôle** , dans la fenêtre Sélectionner une page, cliquez sur **Général**.  
  
3.  Dans la fenêtre des paramètres généraux, dans le champ **Nom** , tapez un nom pour le rôle.  
  
     Par défaut, le nom du rôle par défaut est numéroté de manière incrémentielle pour chaque nouveau rôle. Il est recommandé de taper un nom qui identifie sans ambiguïté le type de membre, par exemple, Directeurs financiers ou Responsables des ressources humaines.  
  
4.  Dans **Définissez les autorisations de base de données pour ce rôle**, sélectionnez l'une des options d'autorisations suivantes :  
  
    |Autorisation|Description|  
    |----------------|-----------------|  
    |**Contrôle total (Administrateur)**|Les membres peuvent apporter des modifications au schéma de modèle et peuvent afficher toutes les données.|  
    |**Traiter la base de données**|Les membres peuvent exécuter les opérations Traiter et Traiter tout. Impossible de modifier le schéma de modèle et d'afficher les données.|  
    |**Lecture**|Les membres sont autorisés à afficher des données (selon les filtres de lignes) mais ne peuvent pas apporter de modifications au schéma de modèle.|  
  
5.  Dans la boîte de dialogue **Créer un rôle** , dans la fenêtre Sélectionner une page, cliquez sur **Appartenance**.  
  
6.  Dans la fenêtre de paramètres d'appartenance, cliquez sur **Ajouter**, puis dans la boîte de dialogue **Sélectionner les utilisateurs ou les groupes** , ajoutez les utilisateurs ou groupes Windows que vous souhaitez ajouter comme membres.  
  
7.  Si le rôle que vous créez dispose d'autorisations de lecture, vous pouvez ajouter des filtres de lignes à une table à l'aide d'une formule DAX. Pour ajouter des filtres de lignes, dans le **propriétés du rôle - \<rolename >** boîte de dialogue **sélectionner une page**, cliquez sur **filtres de lignes**.  
  
8.  Dans la fenêtre de filtres de lignes, sélectionnez une table, puis cliquez sur le **filtre DAX** champ, puis dans le **filtre DAX - \<tablename >** , tapez une formule DAX.  
  
    > [!NOTE]  
    >  Le filtre DAX - \<tablename > champ ne pas contenir un éditeur de requête de la saisie semi-automatique ou fonctionnalité d’insertion. Pour utiliser la saisie semi-automatique lorsque vous écrivez une formule DAX, vous devez utiliser un éditeur de formules DAX dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
9. Cliquez sur **OK** pour enregistrer le rôle.  
  
###  <a name="bkmk_copy_role"></a> Pour copier un rôle  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez la base de données model tabulaire qui contient le rôle que vous souhaitez copier, développez **Rôles**, cliquez avec le bouton droit sur le rôle, puis cliquez sur **Dupliquer**.  
  
###  <a name="bkmk_edit_role"></a> Pour modifier un rôle  
  
-   Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez la base de données model tabulaire qui contient le rôle que vous souhaitez modifier, développez **Rôles**, cliquez avec le bouton droit sur le rôle, puis cliquez sur **Propriétés**.  
  
     Dans le **propriétés du rôle** \<rolename > boîte de dialogue, vous pouvez modifier les autorisations, ajouter ou supprimer des membres, et ajouter/modifier des filtres de lignes.  
  
###  <a name="bkmk_deletet_role"></a> Pour supprimer un rôle  
  
-   Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez la base de données model tabulaire qui contient le rôle que vous souhaitez supprimer, développez **Rôles**, cliquez avec le bouton droit sur le rôle, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
