---
title: Créer une entité (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d85fc4c21f200bcdc5a489cfcee6b50bc9f4b98e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479914"
---
# <a name="create-an-entity-master-data-services"></a>Créer une entité (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une entité destinée à contenir des membres et leurs attributs.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Un modèle doit exister. Pour plus d’informations, consultez [Créer un modèle &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).  
  
### <a name="to-create-an-entity"></a>Pour créer une entité  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Cliquez sur **Ajouter une entité**.  
  
5.  Dans la zone nom de l' **entité** , tapez le nom de l’entité.  
  
6.  Dans la zone **nom des tables de mise en lots** , tapez un nom pour la table de mise en lots.  
  
    > [!TIP]  
    >  Utilisez le nom du modèle dans le nom de la table de mise en lots, par exemple *NomModèle_NomEntité*. Cela facilite la recherche de tables dans la base de données. Pour plus d’informations sur les tables de mise en lots, consultez [&#40;d’importation de données Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
7.  Facultatif. Activez la case à cocher **Créer automatiquement les valeurs de code** . Pour plus d’informations, consultez [création automatique de Code &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).  
  
8.  Dans la liste **activer les hiérarchies explicites et les regroupements** , sélectionnez l’une des options suivantes :  
  
    -   **No**. Sélectionnez cette option si vous n'avez pas besoin d'activer l'entité pour les hiérarchies et les collections explicites. Vous pouvez changer ce paramètre ultérieurement si nécessaire.  
  
    -   **Oui**. Sélectionnez cette option lorsque vous souhaitez activer l'entité pour les hiérarchies et collections explicites. Dans la zone nom de la **hiérarchie explicite** , tapez un nom. Si vous le souhaitez, sélectionnez **hiérarchie obligatoire (tous les membres feuille sont inclus** pour transformer la hiérarchie explicite en hiérarchie obligatoire.  
  
9. Cliquez sur **enregistrer l’entité**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Créer un attribut de texte &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [Créer un attribut de fichier &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Entités &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)   
 [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Modifier le nom d’une entité &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md)   
 [Supprimer une entité &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
