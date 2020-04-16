---
title: Créer une vue d’abonnement (Services de données master) Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c4a2f747192b1cddefeac256d4470a2b345305de
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "65479947"
---
# <a name="create-a-subscription-view-master-data-services"></a>Créer une vue d'abonnement (Master Data Services)
  Créez une vue d’abonnement lorsque vous souhaitez [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] créer une vue de vos données dans la base de données pour une utilisation en souscrivant des systèmes.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Gestion de l'intégration** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, voir [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-subscription-view"></a>Pour créer une vue d'abonnement  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion de l'intégration**.  
  
2.  Dans la barre de menus, cliquez sur **Créer des vues**.  
  
3.  Sur la page **Vues d’abonnement,** cliquez sur **Ajouter la vue d’abonnement**.  
  
4.  Dans le volet **Create Subscription View,** dans la case **nom de l’abonnement,** tapez un nom pour la vue.  
  
5.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
6.  Sélectionnez l’option **Version** ou **Drapeau de version,** puis sélectionnez parmi la liste correspondante.  
  
    > [!TIP]  
    >  Créez une vue d'abonnement selon un indicateur de version. Lorsque vous verrouillez une version, vous pouvez réaffecter l'indicateur à une version ouverte sans mettre à jour la vue d'abonnement.  
  
7.  Sélectionnez l’option de hiérarchie **d’entité** ou **dérivée,** puis sélectionnez parmi la liste correspondante.  
  
8.  Dans la liste **Format** , sélectionnez un format de vue d'abonnement.  
  
9. Si vous avez sélectionné **Niveaux explicites** ou **Niveaux dérivés** dans la liste **Format** , tapez le nombre de niveaux dans la hiérarchie à inclure dans la vue.  
  
10. Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation de données &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)   
 [Supprimer une vue d’abonnement &#40;les services de données master&#41;](delete-a-subscription-view-master-data-services.md)   
 [Créer un indicateur de version &#40;Master Data Services&#41;](create-a-version-flag-master-data-services.md)  
  
  
