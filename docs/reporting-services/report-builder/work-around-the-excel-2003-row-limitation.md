---
title: "Pour contourner la limite de ligne d’Excel 2003 | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8533cd39c8a3d5efde78fee3e045eb744d562a97
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="work-around-the-excel-2003-row-limitation"></a>Work Around the Excel 2003 Row Limitation
  Cette rubrique explique comment contourner la limitation de ligne d’Excel 2003 quand vous exportez des rapports paginés vers Excel. Elle s'applique à un rapport qui ne contient qu'une seule table.  
  
> [!IMPORTANT]  
>  L’extension de rendu [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2003 (.xls) est déconseillée. Pour plus d’informations, consultez [Fonctions déconseillées de SQL Server Reporting Services dans SQL Server 2016](../../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md).  
  
 Excel 2003 prend en charge 65 536 lignes au maximum par feuille. Vous pouvez contourner cette limitation en forçant un saut de page explicite après un certain nombre de lignes. Le convertisseur Excel crée une nouvelle feuille de calcul pour chaque saut de page explicite.  
  
### <a name="to-create-an-explicit-page-break"></a>Pour créer un saut de page explicite  
  
1.  Ouvrez le rapport dans [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] ou dans le portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Cliquez avec le bouton droit sur la ligne de données dans la table, pointez sur **Ajouter un groupe** > **Groupe parent** pour ajouter un groupe de tables externe.  
  
     ![Sélectionnez le groupe Parent](../../reporting-services/report-builder/media/datarow-selectparentgroup.png "sélectionnez le groupe Parent")  
  
3.  Entrez la formule suivante dans la zone d'expression **Regrouper par** , puis cliquez sur **OK** pour ajouter le groupe parent.  
  
     =Int((RowNumber(Nothing)-1)/65000)  
  
     La formule affecte un nombre à chaque ensemble de 65 000 lignes dans le dataset. Quand un saut de page est défini pour le groupe, l'expression insère un saut de page toutes les 65000 lignes.  
  
     En ajoutant le groupe de tables externe, vous ajoutez une colonne de groupe au rapport.  
  
4.  Supprimez la colonne de groupe en cliquant avec le bouton droit sur l’en-tête de la colonne, puis en cliquant sur **Supprimer des colonnes**, **Supprimer les colonnes uniquement**, et enfin sur **OK**.  
  
     ![Supprimer une colonne de groupe](../../reporting-services/report-builder/media/groupcolumn-delete-updated.png "supprimer une colonne de groupe")  
  
5.  Cliquez avec le bouton droit sur **Groupe 1** dans la section **Groupes de lignes** , puis cliquez sur **Propriétés du groupe**.  
  
     ![Afficher les propriétés du groupe](../../reporting-services/report-builder/media/groupproperties-updated.png "afficher les propriétés de groupe")  
  
6.  Dans la page **Tri** de la boîte de dialogue **Propriétés du groupe** , sélectionnez l'option de tri par défaut et cliquez sur **Supprimer**.  
  
     ![Supprimer le tri par défaut](../../reporting-services/report-builder/media/groupproperties-sorting-updated.png "supprimer le tri par défaut")  
  
7.  Dans la page **Sauts de page** , cliquez sur **Entre chaque instance d'un groupe** , puis cliquez sur **OK**.  
  
     ![Définir des sauts de page](../../reporting-services/report-builder/media/groupproperties-pagebreaks-updated.png "définir des sauts de page")  
  
8.  Enregistrez le rapport. Lors de l'exportation vers Excel, plusieurs feuilles de calcul sont créées, chacune contenant un maximum de 65 000 lignes.  
  
  
