---
title: Requérir des valeurs d'attribut
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0e4a49778b9c75c696d079549f586187b1204fd8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73728942"
---
# <a name="require-attribute-values-master-data-services"></a>Requérir des valeurs d'attribut (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], requérez des valeurs d'attribut lorsque vous souhaitez vérifier que vos données de référence sont complètes.  
  
> [!NOTE]  
>  Les membres sans valeurs d'attribut basé sur un domaine ne sont pas affichés dans les hiérarchies dérivées basées sur ces relations.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-require-attribute-values"></a>Pour requérir des valeurs d'attribut  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **règles d’entreprise** , dans la liste déroulante **modèle** , sélectionnez un modèle.  
  
4.  Dans la liste déroulante **Entité** , sélectionnez une entité.  
  
5.  Dans la liste **Types de membres** , sélectionnez un type de membre auquel appliquer la règle d’entreprise.  
  
6.  Cliquez sur **Ajouter**.  
  
7.  Dans la zone **Nom** , tapez un nom de règle d’entreprise.  
  
8.  Si vous le souhaitez, dans le champ **Description** , tapez la description de la règle d’entreprise.  
  
9. Sous le bloc **Then** , cliquez sur le bouton **Ajouter**. Un panneau s’affiche.  
  
10. Dans la liste déroulante **Opérateur** , sélectionnez **action requise**.  
  
11. Dans la liste déroulante **Attribut** , sélectionnez un attribut.  
  
12. Cliquez sur **Save**. Une nouvelle ligne est ajoutée à la grille **Then** .  
  
13. Cliquez sur **Save**.  
  
14. Cliquez sur **Tout publier**.  
  
15. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La valeur de la colonne **État de la règle d’entreprise** est **Active**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Appliquez des règles d'entreprise aux données en suivant l'une de ces procédures :  
  
    -   [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;des règles d’entreprise Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  
