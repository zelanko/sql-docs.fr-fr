---
title: Ajouter des attributs à un groupe de suivi des modifications (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 77a151fe4238c7ed99282436a9668a94d85e2b35
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039748"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>Ajouter des attributs à un groupe de suivi des modifications (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], ajoutez des attributs à un groupe de suivi des modifications lorsque vous souhaitez effectuer le suivi des modifications apportées aux valeurs d'attribut.  
  
> [!NOTE]  
>  Lorsque qu'un attribut est ajouté à un groupe de suivi des modifications et que ses valeurs changent, l'attribut est alors signalé comme modifié dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Créez une règle d'entreprise pour entreprendre une action basée sur la modification.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Les attributs doivent exister pour pouvoir être ajoutés au groupe de suivi des modifications. Pour plus d’informations, consultez [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>Pour ajouter des attributs à un groupe de suivi des modifications  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Sur le **l’Explorateur de modèles** page, dans la barre de menus, pointez sur **gérer** et cliquez sur **entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité pour laquelle vous souhaitez effectuer le suivi des valeurs d'attribut.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Dans la page **Modifier l'entité** :  
  
    -   Si l’attribut concerne les membres feuille, dans le **feuille attributs** volet, sélectionnez l’attribut et cliquez sur **modifier un attribut feuille**.  
  
    -   Si l’attribut est destiné à des membres consolidés, dans le **consolidée des attributs** volet, sélectionnez l’attribut et cliquez sur **modifier l’attribut consolidé**.  
  
    -   Si l’attribut concerne les collections, dans le **attributs de Collection** volet, sélectionnez l’attribut et cliquez sur **attribut de collection modifier**.  
  
7.  Activez la case à cocher **Activer le suivi des modifications** .  
  
8.  Dans la zone **Groupe de suivi des modifications** , tapez un numéro pour le groupe.  
  
9. Cliquez sur **Enregistrer l'attribut**.  
  
10. Dans la page **Maintenance de l'entité** , cliquez sur **Enregistrer l'entité**.  
  
11. Répétez cette procédure pour tous les attributs que vous souhaitez inclure dans le groupe. Utilisez le même numéro de groupe de suivi des modifications pour chaque attribut dans le groupe.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Initier des Actions en fonction de la valeur d’attribut change &#40;Master Data Services&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un attribut de texte &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [Créer un attribut basé sur un domaine &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  