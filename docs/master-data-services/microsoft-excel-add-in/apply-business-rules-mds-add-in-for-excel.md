---
title: "Appliquer des r&#232;gles d&#39;entreprise (Compl&#233;ment MDS pour Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Appliquer des r&#232;gles d&#39;entreprise (Compl&#233;ment MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez appliquer des règles d’entreprise quand vous souhaitez valider les données et confirmer leur validité. Vous pouvez corriger des validations et publier à nouveau les données.  
  
> [!NOTE]  
>  La validation des données se produit automatiquement lorsque vous les publiez. Pour plus d’informations, consultez [Validation &#40;Master Data Services&#41;](../../master-data-services/validation-master-data-services.md).  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir accès à la zone fonctionnelle **Explorateur**.  
  
-   Vous devez disposer d'une feuille de calcul active qui contient des données managées MDS.  
  
### Pour appliquer les règles d'entreprise  
  
1.  Dans le groupe **Publier et valider**, cliquez sur **Appliquer les règles**.  
  
    > [!NOTE]  
    >  Le nombre de membres (lignes) qui sont validés en même temps dépend d'un paramètre dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres de règle d’entreprise](../../master-data-services/system-settings-master-data-services.md#BusinessRules).  
  
2.  Les données sont validées par rapport aux règles d'entreprise et deux colonnes d'état sont affichées. Si ces colonnes ne sont pas affichées automatiquement, dans le groupe **Publier et valider**, cliquez sur **Afficher l’état**.  
  
## Voir aussi  
 [Vue d’ensemble : importation de données à partir d’Excel &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  