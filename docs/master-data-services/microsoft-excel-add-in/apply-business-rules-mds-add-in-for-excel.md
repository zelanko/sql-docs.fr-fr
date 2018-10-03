---
title: Appliquer des règles d’entreprise (Complément MDS pour Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 230553acbe808f8ddd70b18660643c19008ce3dc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47807317"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Appliquer des règles d'entreprise (Complément MDS pour Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] , vous pouvez appliquer des règles d’entreprise quand vous souhaitez valider les données et confirmer leur validité. Vous pouvez corriger des validations et publier à nouveau les données.  
  
> [!NOTE]  
>  La validation des données se produit automatiquement lorsque vous les publiez. Pour plus d’informations, consultez [Validation &#40;Master Data Services&#41;](../../master-data-services/validation-master-data-services.md).  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir accès à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez disposer d'une feuille de calcul active qui contient des données managées MDS.  
  
### <a name="to-apply-business-rules"></a>Pour appliquer les règles d'entreprise  
  
1.  Dans le groupe **Publier et valider** , cliquez sur **Appliquer les règles**.  
  
    > [!NOTE]  
    >  Le nombre de membres (lignes) qui sont validés en même temps dépend d'un paramètre dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres de règle d’entreprise](../../master-data-services/system-settings-master-data-services.md#BusinessRules).  
  
2.  Les données sont validées par rapport aux règles d'entreprise et deux colonnes d'état sont affichées. Si ces colonnes ne sont pas affichées automatiquement, dans le groupe **Publier et valider** , cliquez sur **Afficher l’état** .  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble : importation de données à partir d’Excel &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
