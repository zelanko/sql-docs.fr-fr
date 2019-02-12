---
title: Déplacer les éléments de Page (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 96d3310c489dea5aadc3e9b7e873dbb89ceee9bb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009683"
---
# <a name="move-items-page-report-manager"></a>Page Déplacer les éléments (Gestionnaire de rapports)
  La page Déplacer les éléments vous permet de déplacer un rapport, un dossier ou un autre élément vers un nouvel emplacement sur le serveur de rapports. Vous pouvez taper le chemin d'accès au nouvel emplacement ou utiliser l'arborescence pour naviguer jusqu'à un nouvel emplacement dans l'espace de noms du serveur de rapports. Vous pouvez déplacer uniquement les éléments que vous êtes autorisé à déplacer et qui sont stockés sur le serveur de rapports actuel.  
  
 Lorsque vous déplacez un élément qui est référencé par un autre (par exemple, une source de données partagée ou un modèle qui est référencé par de nombreux rapports), les informations de chemin d'accès relatives à cet élément sont automatiquement mises à jour. Vous pouvez déplacer une source de données partagée sans interrompre la connexion d'une source de données aux rapports et aux modèles qui l'utilisent. Si vous déplacez une source de données partagée ou un modèle vers un dossier pour lequel les utilisateurs n'ont pas d'autorisation, ils seront encore en mesure d'exécuter tout rapport qui référence la source de données ou le modèle, mais ils ne verront pas l'élément dans l'arborescence des dossiers.  
  
 Pour l' **Emplacement**, spécifiez le chemin d'accès complet au dossier, en commençant par le nom du dossier racine. Vous pouvez taper le nom du chemin d'accès ou utiliser l'arborescence pour naviguer jusqu'au dossier désiré.  
  
> [!NOTE]  
>  Il n'est pas possible de déplacer tous les éléments. Vous ne pouvez pas déplacer des dossiers réservés tels que Dossier de base, Mes Rapports ou Dossiers des utilisateurs. En outre, vous ne pouvez pas déplacer un historique de rapport ou des instantanés vers d'autres emplacements. L'historique et les instantanés sont toujours situés au même endroit que le rapport sur lequel ils sont basés et vous ne pouvez y accéder que par l'intermédiaire du rapport.  
  
## <a name="navigation"></a>Navigation  
 Utilisez les procédures suivantes pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-details-view"></a>Pour ouvrir la page Déplacer des éléments dans la page Contenu en Mode Détails  
  
1.  Ouvrez le Gestionnaire de rapports et parcourez l'arborescence jusqu'au dossier qui contient un élément à déplacer. Vous pouvez également déplacer des éléments à partir de la page d'accueil du Gestionnaire de rapports.  
  
2.  Dans la barre d'outils, cliquez sur **Mode Détails**.  
  
    > [!NOTE]  
    >  Si vous voyez uniquement **Mode Mosaïques**, c'est que le **Mode Détails**est déjà activé.  
  
3.  Activez la case à cocher située en regard d'un élément, puis cliquez sur **Déplacer** dans la barre d'outils. Vous pouvez sélectionner plusieurs cases si vous souhaitez déplacer plusieurs éléments vers le même nouvel emplacement.  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-tiles-view"></a>Pour ouvrir la page Déplacer les éléments dans la page Contenu en Mode Mosaïques  
  
1.  Ouvrez le Gestionnaire de rapports et parcourez l'arborescence jusqu'au dossier qui contient un élément à déplacer. Vous pouvez également déplacer des éléments à partir de la page d'accueil du Gestionnaire de rapports.  
  
2.  Dans la barre d'outils, cliquez sur **Mode Mosaïques**.  
  
    > [!NOTE]  
    >  Si vous voyez uniquement **Mode Détails**, c'est que le **Mode Mosaïques**est déjà activé.  
  
3.  Pointez sur un élément et cliquez sur la flèche déroulante.  
  
4.  Dans le menu déroulant, cliquez sur **Déplacer**.  
  
###### <a name="to-open-the-move-items-page-from-the-general-properties-page-of-an-item"></a>Pour ouvrir la page Déplacer les éléments dans la page des propriétés générales d'un élément  
  
1.  Ouvrez le Gestionnaire de rapports et parcourez l'arborescence jusqu'au dossier qui contient un élément à déplacer. Vous pouvez également déplacer des éléments à partir de la page d'accueil du Gestionnaire de rapports.  
  
2.  Pointez sur un élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales pour un élément s'ouvre.  
  
4.  Dans la barre d'outils de l'élément, cliquez sur **Déplacer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Page propriétés générales, dossiers &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md)   
 [Page Propriétés générales, Rapports &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Page propriétés générales, ressources &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md)   
 [Page propriétés générales, des Sources de données partagées &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
