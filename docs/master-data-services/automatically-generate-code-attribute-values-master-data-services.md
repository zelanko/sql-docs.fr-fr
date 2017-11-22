---
title: "Générer automatiquement les valeurs de l’attribut Code (Master Data Services) | Microsoft Docs"
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
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
caps.latest.revision: "5"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 254159f4510b8312310784914afdcd0778cb7fe4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>Générer automatiquement les valeurs de l'attribut Code (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], génère automatiquement les valeurs de l'attribut Code d'une entité lorsque vous souhaitez qu'un entier soit attribué automatiquement à la valeur Code chaque fois qu'un nouveau membre est créé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   L'entité doit exister. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-automatically-generate-code-values"></a>Pour générer automatiquement des valeurs de code  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Sur la page **Gérer les modèles** , sélectionnez la ligne du modèle contenant l’entité que vous souhaitez modifier, puis cliquez sur **Entités**.  
  
3.  Sur la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez générer des codes, puis cliquez sur **Modifier**.  
  
4.  Activez la case à cocher **Créer automatiquement les valeurs de code** .  
  
5.  Dans la zone **Démarrer avec** , tapez un nombre pour démarrer l'incrémentation. Si les membres existent déjà, le code sera défini en fonction de la valeur existante la plus élevée. Par exemple, si la valeur de code existante la plus élevée est 299, la valeur de code du membre suivant sera 300.  
  
6.  Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création automatique de code &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)   
 [Générer automatiquement les valeurs des attributs autres que Code &#40;Master Data Services&#41;](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
