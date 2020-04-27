---
title: Supprimer une règle d’entreprise (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d294bb2d07d87216fb40fb93267518970fdf4c9d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479747"
---
# <a name="delete-a-business-rule-master-data-services"></a>Supprimer une règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], supprimez une règle d'entreprise lorsque vous n'en avez plus besoin.  
  
> [!NOTE]  
>  Vous pouvez empêcher la validation des données par rapport à une règle d'entreprise en l'excluant, plutôt qu'en la supprimant. Pour plus d’informations, consultez [Exclure une règle d’entreprise &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-business-rule"></a>Pour supprimer une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  Dans la liste **Type de membre** , sélectionnez un type de membre auquel appliquer la règle d’entreprise.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Dans la grille, cliquez sur la ligne pour la règle d'entreprise à supprimer.  
  
8.  Cliquez sur **Supprimer la règle d’entreprise sélectionnée**.  
  
9. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La valeur dans la colonne **État** est **suppression en attente**.  
  
10. Cliquez sur **Publier les règles d’entreprise**.  
  
11. Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exclure une règle d’entreprise &#40;Master Data Services&#41;](exclude-a-business-rule-master-data-services.md)   
 [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
