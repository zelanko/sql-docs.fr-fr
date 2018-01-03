---
title: Fusionner les conflits (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 797219ad-5109-4666-94d3-dd1d59440a33
caps.latest.revision: "5"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61a4d43a179d344b89d9a71b67e0ae3ffa1b37b1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="merge-conflicts-master-data-services"></a>Fusionner les conflits (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], si vous essayez de publier des données qui ont été modifiées par un autre utilisateur, la publication échouera avec une erreur de conflit. Pour résoudre cette erreur, vous pouvez exécuter la fonctionnalité Conflits de fusion et publier à nouveau les modifications.  
  
## <a name="prerequisites"></a>Prerequisites  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez disposer au minimum d’une autorisation de mise à jour sur l’objet de modèle feuille de l’entité que vous êtes en train de mettre à jour.  
  
### <a name="to-merge-conflicts"></a>Pour fusionner des conflits  
  
1.  Dans la page **Explorateur** , mettez à jour l’attribut de membre.  
  
2.  Si le même attribut de membre a été modifié par un autre utilisateur, la boîte de dialogue **Fusionner les conflits** apparaît.  
  
3.  Dans la boîte de dialogue **Fusionner les conflits** , vous pouvez effectuer l’une des opérations suivantes :  
  
    -   Choisissez **Dernière** et cliquez sur **Appliquer** si vous voulez annuler les modifications en attente et recharger la dernière version à partir du serveur.  
  
    -   Choisissez **Initiale** et cliquez sur **Appliquer** si vous souhaitez appliquer la version d’origine dans la feuille de calcul.  
  
    -   Choisissez **Les vôtres** et cliquez sur **Appliquer** pour conserver les modifications locales existantes.  
  
4.  Après avoir cliqué sur **Appliquer**, vous pouvez apporter des modifications supplémentaires et réeffectuer la publication. Vous pouvez également cliquer sur **Annuler** si vous souhaitez annuler la mise à jour et recharger la dernière version à partir du serveur.  
  
## <a name="see-also"></a> Voir aussi  
 [Membres &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
  
