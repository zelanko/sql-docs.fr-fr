---
title: Créer un attribut numérique
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating number attributes
- creating number attributes [Master Data Services]
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 608bdd69396f63fdd0389b43e27bacbab0e763f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729589"
---
# <a name="create-a-numeric-attribute-master-data-services"></a>Créer un attribut numérique (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un attribut numérique lorsque vous souhaitez que les utilisateurs entrent un nombre comme valeur d'attribut.  
  
> [!NOTE]  
>  Les attributs numériques ont des limitations. Pour plus d’informations, consultez [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md).  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Une entité doit exister pour créer l'attribut qui lui est destiné. Pour plus d’informations, consultez [créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## <a name="attribute-information"></a>Informations sur les attributs  
 Pour chaque attribut créé, une ligne comportant sept colonnes est ajoutée à la grille. Le tableau suivant décrit les colonnes.  
  
|Colonne|Description|  
|------------|-----------------|  
|Statut|État de l’attribut.<br /><br /> Lorsque vous cliquez sur enregistrer, l’image ![icône d’état de mise à jour](../master-data-services/media/mds-statusicon-updating.png "Icône de mise à jour de l’État") s’affiche, indiquant que l’attribut est en état de mise à jour.<br /><br /> Si des erreurs se produisent lors de la création ou de la modification d’un attribut, l’image ![icône d’état d’erreur](../master-data-services/media/mds-statusicon-error.png "Icône d’état d’erreur") s’affiche.<br /><br /> Dans le cas contraire, l’État est OK et l’image ![icône d’état OK](../master-data-services/media/mds-statusicon-ok.png "Icône d’état OK") s’affiche.|  
|Name|Nom de l'attribut.|  
|Display Name|Nom de l’attribut.|  
|Description|Description de l’attribut.|  
|Largeur d’affichage en pixels|Largeur de l’attribut.|  
|Types et propriétés|Informations sur le type et le type de données de l’attribut.|  
|Activer le suivi des modifications|Spécifie si le suivi des modifications est activé sur l’attribut et indique le numéro du groupe entre parenthèses.|  
  
 Quand vous cliquez sur un attribut, les informations suivantes s’affichent.  
  
-   **Créé par**: nom de l’utilisateur qui a créé l’attribut.  
  
-   Le : date et heure **de**création de l’attribut.  
  
-   **Mise à jour par**: nom de l’utilisateur qui a mis à jour l’attribut pour la dernière fois.  
  
-   Le : date et heure **de**la dernière mise à jour de l’attribut.  
  
### <a name="to-create-a-numeric-attribute"></a>Pour créer un attribut numérique  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Gérer le modèle** , sélectionnez un modèle dans la grille et cliquez sur **Entités**.  
  
3.  Dans la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer un attribut.  
  
4.  Cliquez sur **Attributs**.  
  
5.  Dans la page **Gérer les attributs** , effectuez l’une des opérations suivantes, puis cliquez sur **Ajouter**.  
  
    -   Si l’attribut concerne les membres feuille, sélectionnez **Feuille** dans la zone de liste **Types de membre** .  
  
    -   Si l’attribut concerne les membres consolidés, sélectionnez **Consolidé** dans la zone de liste **Types de membre** .  
  
    -   Si l’attribut concerne les collections, sélectionnez **Collection** dans la zone de liste **Types de membre** .  
  
6.  Dans la zone **Nom** , tapez un nom pour l'attribut. Pour obtenir la liste des mots qui ne doivent pas être utilisés comme noms d’attribut, consultez [Mots réservés &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
7.  Si vous le souhaitez, tapez le nom complet et une description de l’attribut dans le champ **Description** .  
  
8.  Dans la zone **Largeur d'affichage en pixels** , tapez la largeur de la colonne d'attribut à afficher dans la grille **Explorateur** .  
  
9. Dans la liste **Type d’attribut** , sélectionnez **Forme libre**.  
  
10. Dans la liste **Type de données** , sélectionnez **Nombre**.  
  
11. Dans la zone **Décimales** , tapez le nombre de chiffres qui peuvent être entrés après la virgule décimale.  
  
12. Dans la zone de liste **Masque d’entrée** , sélectionnez le format des nombres négatifs.  
  
13. Sélectionnez éventuellement **Activer le suivi des modifications** pour effectuer le suivi des modifications apportées aux groupes d'attributs. Pour plus d’informations, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
14. Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Modifiez le nom d’un attribut et le type de données &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Créer un attribut de fichier &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
