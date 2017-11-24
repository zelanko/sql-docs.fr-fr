---
title: "Supprimer une règle d’entreprise (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 24617e8cdf46bcb5efb9b1466bcedc96583ee5ce
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="delete-a-business-rule-master-data-services"></a>Supprimer une règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], supprimez une règle d'entreprise lorsque vous n'en avez plus besoin.  
  
> [!NOTE]  
>  Vous pouvez empêcher la validation des données par rapport à une règle d'entreprise en l'excluant, plutôt qu'en la supprimant. Pour plus d’informations, consultez [Exclure une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-business-rule"></a>Pour supprimer une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Règles d’entreprise** , sélectionnez un modèle dans la liste déroulante **Modèle** .  
  
4.  Dans la liste déroulante **Entité** , sélectionnez une entité.  
  
5.  Dans la liste **Types de membres** , sélectionnez un type de membre auquel appliquer la règle d’entreprise.  
  
6.  Dans la grille, cliquez sur la ligne pour la règle d'entreprise à supprimer.  
  
7.  Cliquez sur **Supprimer**.  
  
8.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La valeur de la colonne **État de la règle d’entreprise** est **Suppression en attente**.  
  
9. Cliquez sur **Tout publier**.  
  
10. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La règle d’entreprise supprimée n’est plus affichée dans la grille.  
  
## <a name="see-also"></a>Voir aussi  
 [Exclure une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md)   
 [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
