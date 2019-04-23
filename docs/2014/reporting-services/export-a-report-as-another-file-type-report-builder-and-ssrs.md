---
title: Exporter un rapport en tant que Type d’un autre fichier (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: b577568b-ecbd-44c3-be88-31dab6fc38a2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a26b183d3024333f5792203e180df395c0301892
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59948905"
---
# <a name="export-a-report-as-another-file-type-report-builder-and-ssrs"></a>Exporter un rapport dans un autre type de fichier (Générateur de rapports et SSRS)
  Vous pouvez effectuer le rendu d'un rapport dans un autre format de fichier, tel que CSV, Image, PDF, [!INCLUDE[ofprword](../includes/ofprword-md.md)]ou [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], en affichant un aperçu de votre rapport dans le Générateur de rapports ou le Concepteur de rapports, ou vous pouvez effectuer le rendu du rapport en visualisant le rapport sur le serveur de rapports. Le rendu du rapport dans un format spécifique est utile lorsque vous souhaitez enregistrer immédiatement le rapport dans un autre type de fichier sans le publier sur le serveur de rapports ou lorsque vous souhaitez voir l'aspect de votre conception de rapport une fois remis aux lecteurs du rapport dans un format spécifique. Le rendu du rapport sur le serveur de rapports est utile lorsque vous définissez des abonnements ou remettez vos rapports via messagerie électronique, ou si vous souhaitez enregistrer un rapport qui est disponible sur le serveur de rapports. Pour plus d’informations, consultez [Abonnements et remise &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-export-a-report-as-another-file-type-in-report-builder"></a>Pour exporter un rapport dans un autre type de fichier dans le Générateur de rapports  
  
1.  Affichez l'aperçu du rapport.  
  
2.  Cliquez sur **Exporter**dans le ruban.  
  
3.  Sélectionnez le format que vous souhaitez utiliser.  
  
     La boîte de dialogue **Enregistrer sous** s'affiche. Par défaut, le nom du fichier correspond à celui du rapport que vous avez exporté. Vous pouvez éventuellement modifier le nom du fichier.  
  
4.  Accédez à l'emplacement où vous avez enregistré le rapport exporté et ouvrez-le.  
  
> [!NOTE]  
>  Si le programme ne peut pas ouvrir le rapport dans le format que vous avez choisi car aucun programme n'est associé à ce type de fichier, vous êtes invité à enregistrer le rapport exporté ou à rechercher un programme en ligne pour ouvrir le rapport.  
  
### <a name="to-export-a-report-as-another-file-type-in-report-manager"></a>Pour exporter un rapport dans un autre type de fichier dans le Gestionnaire de rapports  
  
1.  À partir du Gestionnaire de rapports, affichez la page **Accueil** et naviguez jusqu'au rapport que vous souhaitez exporter.  
  
2.  Cliquez sur le rapport.  
  
     Le rapport est généré.  
  
3.  Dans la barre d'outils Visionneuse de rapports, cliquez sur la flèche déroulante **Sélectionner un format** .  
  
4.  Sélectionnez le format que vous souhaitez utiliser.  
  
5.  Cliquez sur **Exporter**.  
  
     Un message s'affiche qui vous demande si vous souhaitez ouvrir ou enregistrer le fichier.  
  
6.  Pour afficher le rapport dans le format d'exportation sélectionné, cliquez sur **Ouvrir**.  
  
     \- ou -  
  
     Pour enregistrer immédiatement le rapport dans le format d'exportation sélectionné, cliquez sur **Enregistrer**.  
  
     À l'aide de l'application associée au format que vous avez choisi, le rapport est affiché ou enregistré. Si vous cliquez sur **Enregistrer**, vous devrez indiquer un emplacement pour enregistrer votre rapport.  
  
     **Remarque** Si le programme ne peut pas ouvrir le rapport dans le format que vous avez choisi car vous ne disposez pas d'un programme associé à ce type de fichier, vous serez invité à enregistrer le rapport exporté ou à rechercher un programme en ligne pour ouvrir le rapport.  
  
### <a name="to-export-a-report-as-another-file-type-in-a-sharepoint-library"></a>Pour exporter un rapport dans un autre type de fichier dans une bibliothèque SharePoint  
  
1.  Affichez l'aperçu du rapport.  
  
2.  Dans la barre d'outils, cliquez sur **Actions**, pointez sur **Exporter**, puis sélectionnez le format à utiliser.  
  
     La boîte de dialogue **Téléchargement de fichiers** s'affiche.  
  
3.  Pour afficher le rapport dans le format d'exportation sélectionné, cliquez sur **Ouvrir**.  
  
     \- ou -  
  
     Pour enregistrer immédiatement le rapport dans le format d'exportation sélectionné, cliquez sur **Enregistrer**.  
  
     À l'aide de l'application associée au format que vous avez choisi, le rapport est affiché ou enregistré. Si vous cliquez sur **Enregistrer**, vous devrez indiquer un emplacement pour enregistrer votre rapport.  
  
     Modifiez éventuellement le nom de fichier du rapport exporté.  
  
     **Remarque** Si le programme ne peut pas ouvrir le rapport dans le format que vous avez choisi car vous ne disposez pas d'un programme associé à ce type de fichier, vous serez invité à enregistrer le rapport exporté ou à rechercher un programme en ligne pour ouvrir le rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation de rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)   
 [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Fonctionnalité interactive des différentes Extensions de rendu de rapport &#40;Générateur de rapports et SSRS&#41;](report-builder/interactive-functionality-different-report-rendering-extensions.md)  
  
  
