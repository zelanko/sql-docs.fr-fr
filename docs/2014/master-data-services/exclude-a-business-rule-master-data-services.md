---
title: Exclure une règle d’entreprise (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 6285d32ca514cacef4b78b31336bb33866baf860
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52800701"
---
# <a name="exclude-a-business-rule-master-data-services"></a>Exclure une règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], excluez une règle d'entreprise lorsque vous ne voulez pas supprimer la règle définitivement, mais que vous ne souhaitez pas valider des données par rapport à elle.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-exclude-a-business-rule"></a>Pour exclure une règle d'entreprise  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** et cliquez sur **Règles d'entreprise**.  
  
3.  Dans la page **Maintenance des règles d’entreprise** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  À partir de la **Type de membre** , sélectionnez un type de membre.  
  
6.  Dans la liste **Attribut** , sélectionnez un attribut ou conservez l’option par défaut **Tout**.  
  
7.  Dans la grille, dans la ligne de la règle d’entreprise, sélectionnez la case à cocher dans la **exclure** colonne. La valeur dans le **état** colonne est **Exclusion en attente**.  
  
8.  Cliquez sur **Publier les règles d’entreprise**.  
  
9. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. La valeur dans le **état** colonne est **exclu**.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)   
 [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
