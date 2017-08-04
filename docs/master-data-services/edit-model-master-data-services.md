---
title: "Modifier le modèle (Master Data Services) | Documents Microsoft"
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
- models [Master Data Services], changing name
ms.assetid: 399eed32-7c61-4239-9c06-996a65219518
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 08291f09ed7bc172fe22534e82b79ecc47ce55e1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="edit-model-master-data-services"></a>Modifier le modèle (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez modifier le nom et la description d’un modèle et indiquer la durée de conservation des journaux des transactions.  
  
 Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-a-model"></a>Pour modifier un modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Modèles**.  
  
3.  Sur la page **Gérer les modèles** , dans la grille, sélectionnez la ligne correspondant au modèle dont vous souhaitez modifier le nom ou la description.  
  
4.  Cliquez sur **Modifier**.  
  
5.  Dans la zone **Nom** , tapez le nom mis à jour du modèle.  
  
6.  Dans le champ **Description** , tapez la description mise à jour du modèle.  
  
7.  Dans le champ **Nombre de jours de rétention du journal** , sélectionnez l’une des options permettant de conserver les données du journal. La valeur par défaut est **Paramètre système**, ce qui indique que la valeur est héritée des paramètres système dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
     Pour remplacer le paramètre système sans supprimer les données du journal des transactions, sélectionnez **NON**. Pour conserver uniquement les données du journal d’aujourd’hui et effacer celles des jours précédents, sélectionnez **OUI** et réglez le champ **Jours** sur 0. Pour conserver les données du journal pendant un nombre de jours déterminé, sélectionnez **OUI** et réglez le champ **Jours** sur le nombre de jours souhaité.  
  
8.  Cliquez sur **Enregistrer le modèle**.  
  
 La colonne **État** de la grille affiche l’état de l’opération sur le modèle. Lorsque vous cliquez sur le **enregistrer le modèle** bouton, le ![mise à jour](../master-data-services/media/mds-model-status-updating.png "mise à jour") image est affichée, ce qui signifie que le modèle est mise à jour. S’il existe des erreurs lors de la création ou modification d’un modèle, le ![erreur](../master-data-services/media/mds-model-status-error.png "erreur") image est affichée. Dans le cas contraire, le statut est OK et l’image ![OK](../master-data-services/media/mds-model-status-ok.png "OK") apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un modèle de &#40; Master Data Services &#41;](../master-data-services/create-a-model-master-data-services.md)   
 [Supprimer un modèle de &#40; Master Data Services &#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Modèles (Master Data Services)](../master-data-services/models-master-data-services.md)  
  
  
