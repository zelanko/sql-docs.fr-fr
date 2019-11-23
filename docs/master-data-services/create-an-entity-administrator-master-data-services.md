---
title: Créer un administrateur d’entité
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 717be1e8-488e-4219-8d1e-ca9084b864cd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bca3fbbfe08969f27c26ab0ca6a66e76468acdc8
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729535"
---
# <a name="create-an-entity-administrator-master-data-services"></a>Créer un administrateur d’entité (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un administrateur d’entité lorsque vous souhaitez qu’un groupe ou un utilisateur dispose de toutes les autorisations concernant tous les objets dans une ou plusieurs entités, ou de l’autorisation permettant d’approuver les ensembles de modification en attente.  
  
> [!TIP]  
>  Pour simplifier l’administration, créez un groupe Windows ou local et configurez-le en tant qu’administrateur d’entité. Vous pouvez ensuite ajouter et supprimer des utilisateurs dans le groupe sans accéder à l'interface utilisateur de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
## <a name="to-create-an-entity-administrator"></a>Pour créer un administrateur d’entité  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Sélectionnez la ligne correspondant à l’utilisateur ou au groupe à modifier, puis cliquez sur **Modifier l’utilisateur sélectionné**.  
  
3.  Cliquez sur l’onglet **Modèles** , sélectionnez un modèle dans la liste **Modèles** , le cas échéant, puis cliquez sur **Modifier**.  
  
4.  Cliquez sur l’entité à laquelle vous souhaitez accorder des autorisations, puis cliquez sur l’option **Admin** dans le menu.  
  
5.  Effectuez l’étape 4 pour chaque entité que le groupe ou l’administrateur doit gérer.  
  
6.  Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)   
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Autorisations des membres de la hiérarchie &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
