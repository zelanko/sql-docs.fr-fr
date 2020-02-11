---
title: Appliquer des règles d’entreprise (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 32819a694769092c255c4b2ed918dd8fde99362e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482602"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Appliquer des règles d'entreprise (Complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , vous pouvez appliquer des règles d’entreprise quand vous souhaitez valider les données et confirmer leur validité. Vous pouvez corriger des validations et publier à nouveau les données.  
  
> [!NOTE]  
>  La validation des données se produit automatiquement lorsque vous les publiez. Pour plus d’informations, consultez [Procédure stockée de validation &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir accès à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez disposer d'une feuille de calcul active qui contient des données managées MDS.  
  
### <a name="to-apply-business-rules"></a>Pour appliquer les règles d'entreprise  
  
1.  Dans le groupe **Publier et valider** , cliquez sur **Appliquer les règles**.  
  
    > [!NOTE]  
    >  Le nombre de membres (lignes) qui sont validés en même temps dépend d'un paramètre dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres de règle d’entreprise](../system-settings-master-data-services.md#BusinessRules).  
  
2.  Les données sont validées par rapport aux règles d'entreprise et deux colonnes d'état sont affichées. Si ces colonnes ne sont pas affichées automatiquement, dans le groupe **Publier et valider** , cliquez sur **Afficher l’état** .  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des Complément MDS pour Excel de &#40;de données&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
