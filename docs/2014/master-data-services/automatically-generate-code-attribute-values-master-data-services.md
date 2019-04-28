---
title: Générer automatiquement les valeurs de l’attribut Code (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: bc686928863395217fa564ff04b7c26a52c1f1bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877256"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>Générer automatiquement les valeurs de l'attribut Code (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], générez automatiquement les valeurs de l’attribut Code d’une entité quand vous souhaitez qu’un entier soit attribué automatiquement à la valeur Code chaque fois qu’un membre est créé.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   L'entité doit exister. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-automatically-generate-code-values"></a>Pour générer automatiquement des valeurs de code  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Sur le **l’Explorateur de modèles** page, dans la barre de menus, pointez sur **gérer** et cliquez sur **entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité pour laquelle vous voulez générer les codes.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Activez la case à cocher **Créer automatiquement les valeurs de code** .  
  
7.  Dans la zone **Démarrer avec** , tapez un nombre pour démarrer l'incrémentation. Si les membres existent déjà, le code sera défini en fonction de la valeur existante la plus élevée. Par exemple, si la valeur de code existante la plus élevée est 299, la valeur de code du membre suivant sera 300.  
  
8.  Cliquez sur **enregistrer l’entité**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création automatique de code &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)   
 [Générer automatiquement les valeurs des attributs autres que Code &#40;Master Data Services&#41;](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
