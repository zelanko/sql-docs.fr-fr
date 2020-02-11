---
title: Création d'un modèle
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 730e18fca866891d62b68d321ec13e4be5da59bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728483"
---
# <a name="create-a-model-master-data-services"></a>Créer un modèle (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un modèle destiné à contenir des objets de modèle.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model"></a>Pour créer un modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Modèles**.  
  
3.  Sur la page **Gérer les modèles** , cliquez sur **Ajouter**. Un panneau s’affiche à droite.  
  
4.  Dans la zone **Nom** , tapez le nom du modèle.  
  
5.  (Facultatif) Dans le champ **Description** , saisissez la description du modèle.  
  
6.  Dans le champ **Nombre de jours de rétention du journal** , sélectionnez l’une des options permettant de conserver les données du journal. La valeur par défaut est **Paramètre système**, ce qui indique que la valeur est héritée des paramètres système dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
     Pour remplacer le paramètre système sans supprimer les données du journal des transactions, sélectionnez **NON**. Pour conserver uniquement les données du journal d’aujourd’hui et effacer celles des jours précédents, sélectionnez **OUI** et réglez le champ **Jours** sur 0. Pour conserver les données du journal pendant un nombre de jours déterminé, sélectionnez **OUI** et réglez le champ **Jours** sur le nombre de jours souhaité.  
  
7.  Sélectionnez éventuellement **Créer une entité portant le même nom que le modèle** pour créer une entité du même nom que le modèle.  
  
8.  Cliquez sur **Enregistrer le modèle**.  
  
 Pour chaque modèle créé, une ligne comportant huit colonnes est ajoutée à la grille. Ces huit colonnes sont les suivantes :  
  
-   **État**: état du modèle. Lorsque vous cliquez sur le bouton **enregistrer le modèle** , l’image de ![mise à jour](../master-data-services/media/mds-model-status-updating.png "Mise à jour") s’affiche, indiquant que le modèle est en mode de mise à jour. Si des erreurs se produisent lors de la création ou de la modification d’un modèle, l’image d' ![erreur](../master-data-services/media/mds-model-status-error.png "Error") s’affiche. Dans le cas contraire, l’état est OK et l’image ![OK](../master-data-services/media/mds-model-status-ok.png "OK") apparaît.  
  
-   **Nom**: nom du modèle.  
  
-   **Description**: la description du modèle.  
  
-   **Jours de rétention du journal**: nombre de jours pendant lesquels le journal est conservé pour le modèle.  
  
-   **Créé par**: nom d’utilisateur de l’utilisateur qui a créé le modèle.  
  
-   **Date et heure de création**: date et heure de création du modèle.  
  
-   **Mise à jour par**: nom d’utilisateur de l’utilisateur qui a mis à jour le modèle pour la dernière fois.  
  
-   **Date et heure de mise à jour**: date et heure de la dernière mise à jour du modèle.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Entités &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)   
 [Supprimer un modèle &#40;Master Data Services&#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Modifier le modèle &#40;Master Data Services&#41;](../master-data-services/edit-model-master-data-services.md)   
 [Transactions &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md)  
  
  
