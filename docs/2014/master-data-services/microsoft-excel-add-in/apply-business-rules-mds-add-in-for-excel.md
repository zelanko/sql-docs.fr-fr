---
title: Appliquer des règles d’entreprise (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2722e678de98bbfbf5a1181a69101fbe2a9427d8
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52797921"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Appliquer des règles d'entreprise (Complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , vous pouvez appliquer des règles d’entreprise quand vous souhaitez valider les données et confirmer leur validité. Vous pouvez corriger des validations et publier à nouveau les données.  
  
> [!NOTE]  
>  La validation des données se produit automatiquement lorsque vous les publiez. Pour plus d’informations, consultez [Procédure stockée de validation &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir accès à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez disposer d'une feuille de calcul active qui contient des données managées MDS.  
  
### <a name="to-apply-business-rules"></a>Pour appliquer les règles d'entreprise  
  
1.  Dans le groupe **Publier et valider** , cliquez sur **Appliquer les règles**.  
  
    > [!NOTE]  
    >  Le nombre de membres (lignes) qui sont validés en même temps dépend d'un paramètre dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres de règle d’entreprise](../system-settings-master-data-services.md#BusinessRules).  
  
2.  Les données sont validées par rapport aux règles d'entreprise et deux colonnes d'état sont affichées. Si ces colonnes ne sont pas affichées automatiquement, dans le groupe **Publier et valider** , cliquez sur **Afficher l’état** .  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de données &#40;complément MDS pour Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
