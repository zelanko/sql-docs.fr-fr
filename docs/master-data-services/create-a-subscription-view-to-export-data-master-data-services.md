---
title: "Créer une vue d’abonnement pour exporter des données (Master Data Services) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4934e49ef7b8e4f6b56439dd3b414fc93d5af832
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-subscription-view-to-export-data-master-data-services"></a>Créer une vue d’abonnement pour exporter des données (Master Data Services)
  Créez une vue d’abonnement pour exporter les données Master Data Services vers des systèmes d’abonnement. Vous créez une vue de vos données dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="prerequisites"></a>Composants requis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Gestion de l'intégration** . Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-and-edit-a-subscription-view"></a>Pour créer et modifier une vue d’abonnement  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion de l'intégration**.  
  
2.  Dans la barre de menus, cliquez sur **Créer des vues**.  
  
3.  Dans la page **Vues d’abonnement** , cliquez sur **Ajouter** si vous souhaitez créer une vue, ou cliquez sur **Modifier** pour modifier une vue. Un panneau s’affiche sur le côté droit.  
  
4.  Dans la zone **Nom** du volet **Créer une vue d’abonnement** , tapez un nom pour la vue.  
  
     Dans la zone **Nom** du volet **Modifier une vue d’abonnement** , tapez le nouveau nom de la vue.  
  
5.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
6.  Sélectionnez **Inclure les membres supprimés récupérables**pour inclure dans la vue les membres qui ont fait l’objet d’une suppression réversible.  
  
7.  Dans **Options de version** , sélectionnez **Version** ou **Indicateur de version**, puis effectuez votre sélection dans la liste correspondante.  
  
    > [!TIP]  
    >  Créez une vue d'abonnement selon un indicateur de version. Lorsque vous verrouillez une version, vous pouvez réaffecter l'indicateur à une version ouverte sans mettre à jour la vue d'abonnement.  
  
8.  Dans l’option **Sources de données** , sélectionnez **Entité** ou **Hiérarchie dérivée** , puis effectuez votre sélection dans la liste correspondante.  
  
9. Dans la liste **Format** , sélectionnez un format de vue d'abonnement.  
  
10. Si vous avez sélectionné **Niveaux explicites** ou **Niveaux dérivés** dans la liste **Format** , tapez le nombre de niveaux dans la hiérarchie à inclure dans la vue.  
  
11. Cliquez sur **Enregistrer**.  
  
## <a name="view-information"></a>Visualiser les informations  
 Pour chaque vue créée, une ligne comportant dix colonnes est ajoutée à la grille. Le tableau ci-après décrit ces colonnes.  
  
|Colonne|Description|  
|------------|-----------------|  
|État|État de la vue.<br /><br /> Lorsque vous cliquez sur **enregistrer**, le ![icône de mise à jour d’état](../master-data-services/media/mds-statusicon-updating.png "icône de mise à jour d’état") image s’affiche, indiquant que la vue est mise à jour.<br /><br /> S’il existe des erreurs lors de la création ou la modification d’une vue, le ![icône de statut d’erreur](../master-data-services/media/mds-statusicon-error.png "icône de statut d’erreur") image s’affiche.<br /><br /> Dans le cas contraire, l’état est OK et la ![icône pour l’état OK](../master-data-services/media/mds-statusicon-ok.png "icône pour l’état OK") image s’affiche.|  
|Nom|Nom de la vue d’abonnement.|  
|Modèle|Nom du modèle.|  
|Options de version|Nom de la version.|  
|Version|Nom de l’indicateur de version.|  
|Entité|Nom de la hiérarchie dérivée.|  
|Sources de données|Nom de l’entité.|  
|Format|Type des données figurant dans la vue.|  
|Level|Spécifie le nombre de niveaux de la vue ; cette valeur est uniquement utilisée pour les formats de vue de niveau Explicite ou Dérivé.|  
|Inclure les membres supprimés|Indique si les membres supprimés de façon réversible sont inclus dans la vue.|  
  
 Lorsque vous cliquez sur une vue, les informations ci-après s’affichent.  
  
-   **Créée par**: nom de l’utilisateur ayant créé la vue.  
  
-   **Le**: date et heure de création de la vue.  
  
-   **Mise à jour par**: nom de l’utilisateur ayant effectué la dernière mise à jour de la vue.  
  
-   **Le**: date et heure de la dernière mise à jour de la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : exportation de données &#40;Master Data Services&#41;](../master-data-services/overview-exporting-data-master-data-services.md)   
 [Supprimer une vue d’abonnement &#40; Master Data Services &#41;](../master-data-services/delete-a-subscription-view-master-data-services.md)   
 [Créer un indicateur de Version &#40; Master Data Services &#41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
  
