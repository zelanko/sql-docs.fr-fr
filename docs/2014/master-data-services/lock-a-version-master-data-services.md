---
title: Verrouiller une version (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 23e705dd936383db09b0a9eda37eb6d925dbffbb
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750871"
---
# <a name="lock-a-version-master-data-services"></a>Verrouiller une version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], verrouillez une version d’un modèle pour empêcher que des modifications ne soient apportées aux membres du modèle et à leurs attributs.  
  
> [!NOTE]  
>  Lorsqu'une version est verrouillée, les administrateurs de modèle peuvent continuer à ajouter, modifier et supprimer des membres. Les autres utilisateurs qui ont une autorisation sur le modèle peuvent consulter les membres uniquement.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   L’état de la version doit être **Ouvert**.  
  
### <a name="to-lock-a-version"></a>Pour verrouiller une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions** , sélectionnez la ligne de la version à verrouiller.  
  
3.  Cliquez sur **Verrouiller**.  
  
4.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Activer une version &#40;Master Data Services&#41;](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Déverrouiller une version &#40;Master Data Services&#41;](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
