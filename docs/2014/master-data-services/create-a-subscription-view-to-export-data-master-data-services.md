---
title: Créer une vue d’abonnement (Master Data Services) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0b79bd1e50871fb921a3ce2b3fe9e43ab0995a9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143295"
---
# <a name="create-a-subscription-view-master-data-services"></a>Créer une vue d'abonnement (Master Data Services)
  Créer une vue d’abonnement lorsque vous souhaitez créer une vue de vos données dans le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données pour une utilisation par les systèmes d’abonnement.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Gestion de l'intégration** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-subscription-view"></a>Pour créer une vue d'abonnement  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion de l'intégration**.  
  
2.  Dans la barre de menus, cliquez sur **Créer des vues**.  
  
3.  Sur le **vues d’abonnement** , cliquez sur **ajouter une vue d’abonnement**.  
  
4.  Dans le **créer une vue d’abonnement** volet, dans le **nom de vue d’abonnement** , tapez un nom pour la vue.  
  
5.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
6.  Sélectionnez le **Version** ou **indicateur de Version** option et sélectionnez dans la liste correspondante.  
  
    > [!TIP]  
    >  Créez une vue d'abonnement selon un indicateur de version. Lorsque vous verrouillez une version, vous pouvez réaffecter l'indicateur à une version ouverte sans mettre à jour la vue d'abonnement.  
  
7.  Sélectionnez le **entité** ou **hiérarchie dérivée** option et sélectionnez dans la liste correspondante.  
  
8.  Dans la liste **Format** , sélectionnez un format de vue d'abonnement.  
  
9. Si vous avez sélectionné **Niveaux explicites** ou **Niveaux dérivés** dans la liste **Format** , tapez le nombre de niveaux dans la hiérarchie à inclure dans la vue.  
  
10. Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation de données &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)   
 [Supprimer une vue d’abonnement &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md)   
 [Créer un indicateur de Version &#40;Master Data Services&#41;](create-a-version-flag-master-data-services.md)  
  
  