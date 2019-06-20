---
title: Déployer un package de déploiement de modèle à l’aide de l’Assistant | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], deploying
- models [Master Data Services], deploying a package
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cbdf233af3c0c27d6b4e95d18dc2c438d5307e7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65479484"
---
# <a name="deploy-a-model-deployment-package-by-using-the-wizard"></a>Déployer un package de déploiement de modèle à l'aide de l'Assistant
  Utilisez l'Assistant Déploiement de modèle [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour déployer les packages qui contiennent uniquement des objets de modèle. Si vous avez besoin de déployer un package avec des données, consultez [Déployer un package de déploiement de modèle à l’aide de MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]  
>  Les packages peuvent être déployés uniquement dans l'édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans laquelle ils ont été créés. Cela signifie que les packages créés dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ne peuvent pas être déployés sur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** dans l'environnement [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] cible.  
  
-   Un package de déploiement de modèle doit exister. Pour plus d’informations, consultez [Créer un package de déploiement de modèle à l’aide de l’Assistant](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
  
-   Vous devez être administrateur dans l'environnement où vous déployez le modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-deploy-a-model-deployment-package-of-model-objects-only"></a>Pour déployer un package de déploiement de modèle d'objets de modèle uniquement  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Système** , puis cliquez sur **Déploiement**.  
  
3.  Dans l' **Assistant Déploiement de modèle**, cliquez sur **Déployer**.  
  
4.  Cliquez sur **Parcourir**.  
  
5.  Recherchez votre package de déploiement (fichier .pkg), puis cliquez sur **Ouvrir**.  
  
6.  Cliquer sur **Suivant**.  
  
7.  Une fois le package chargé, cliquez sur **Suivant**.  
  
8.  Si le modèle existe déjà, vous pouvez le mettre à jour en sélectionnant **Mettre à jour le modèle existant**. Pour créer un modèle, sélectionnez **Créer un modèle** , cliquez sur **Suivant** , puis tapez un nom pour le nouveau modèle.  
  
9. Cliquez sur **Terminer** pour quitter l'Assistant.  
  
 **Remarques :**  
  
-   Si une vue d’abonnement dans le package a le même nom qu’une vue d’abonnement dans un modèle existant, la vue est créée en tant que *modelname.subscriptionviewname*. Si ce nom existe déjà, la vue d'abonnement n'est pas créée.  
  
-   Le processus de déploiement comporte quatre étapes :  
  
    1.  Les objets de modèle sont créés.  
  
    2.  Les vues d'abonnement sont créées.  
  
    3.  Les règles d'entreprise sont créées.  
  
    4.  Les données de référence sont remplies.  
  
-   Lorsque vous créez un modèle nouveau ou cloné, si le processus échoue au cours d'une étape, le modèle est supprimé.  
  
     Lorsque vous mettez à jour un modèle, si le processus échoue au cours des trois premières étapes, il s'arrête ; toutefois, les modifications qui sont déjà effectuées ne sont pas annulées. Si le processus échoue à l'étape 4, les membres qui peuvent être mis à jour sont mis à jour.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Les métadonnées définies par l'utilisateur, les attributs de fichier et les autorisations d'accès ne sont pas inclus dans les packages de déploiement de modèle. Après avoir déployé un modèle, vous devez les mettre à jour manuellement. Pour plus d'informations, consultez :  
  
-   [Ajouter des métadonnées &#40;Master Data Services&#41;](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de modèles &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
