---
title: Créer un indicateur de version (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d5e30a0161202613ca4cab361733c1786c4ae90
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971746"
---
# <a name="create-a-version-flag-master-data-services"></a>Créer un indicateur de version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un indicateur de version à affecter à une version. L’indicateur peut spécifier la version que les utilisateurs ou les systèmes d’abonnement doivent utiliser.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>Pour créer un indicateur de version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Indicateurs**.  
  
3.  Dans la page **Gérer les indicateurs de version** , dans le champ **Modèle** , sélectionnez le modèle pour lequel vous souhaitez créer un indicateur.  
  
4.  Cliquez sur **Add**.  
  
5.  Renseignez la zone **Nom** .  
  
6.  Dans la zone **Description**, tapez une description.  
  
7.  Dans le champ **Versions activées uniquement** , sélectionnez **True** pour spécifier que l’indicateur ne peut être affecté qu’aux versions présentant l’état **Activé** . Sélectionnez **False** pour indiquer que l’indicateur peut être affecté aux versions présentant n’importe quel état.  
  
8.  Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Affecter un indicateur à une version &#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Modifier le nom d’un indicateur de version &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
