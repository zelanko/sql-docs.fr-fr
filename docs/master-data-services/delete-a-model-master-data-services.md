---
title: "Supprimer un modèle (Master Data Services) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting models [Master Data Services]
- models [Master Data Services], deleting models
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: be50aa7e9de502b0db2cb427bf894081196b579e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="delete-a-model-master-data-services"></a>Supprimer un modèle (Master Data Services)
  Supprimez un modèle afin de supprimer le modèle et toutes ses données de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
> [!NOTE]  
>  Lorsque vous effectuez cette procédure, tous les objets et toutes les données de toutes les versions du modèle sont supprimés définitivement.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-model"></a>Pour supprimer un modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Modèles**.  
  
3.  Dans la grille de la page **Gérer les modèles** , sélectionnez la ligne du modèle à supprimer.  
  
4.  Cliquez sur **Supprimer**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue de confirmation supplémentaire, cliquez sur **OK**.  
  
 La colonne **État** de la grille affiche l’état de l’opération sur le modèle. Lorsque vous cliquez sur le **enregistrer le modèle** bouton, le ![mise à jour](../master-data-services/media/mds-model-status-updating.png "mise à jour") image est affichée, ce qui signifie que le modèle est mise à jour. S’il existe des erreurs lors de la création ou modification d’un modèle, le ![erreur](../master-data-services/media/mds-model-status-error.png "erreur") image est affichée. Dans le cas contraire, le statut est OK et l’image ![OK](../master-data-services/media/mds-model-status-ok.png "OK") apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles &#40; Master Data Services &#41;](../master-data-services/models-master-data-services.md)   
 [Créer un modèle de &#40; Master Data Services &#41;](../master-data-services/create-a-model-master-data-services.md)  
  
  
