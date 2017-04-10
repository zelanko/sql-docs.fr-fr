---
title: "Ajouter une r&#233;f&#233;rence d&#39;assembly &#224; un rapport (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "code [Reporting Services]"
  - "assemblys personnalisés [Reporting Services], référencement"
  - "code personnalisé [Reporting Services]"
  - "ajout de références d'assembly"
  - "assemblys [Reporting Services], références"
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
caps.latest.revision: 43
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 43
---
# Ajouter une r&#233;f&#233;rence d&#39;assembly &#224; un rapport (SSRS)
  Lorsque vous incorporez du code personnalisé qui contient des références aux classes [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] qui ne sont pas dans <xref:System.Math> ou <xref:System.Convert>, vous devez fournir une référence d’assembly au rapport afin que le processeur de rapports puisse résoudre les noms. Pour plus d’informations, consultez [Ajouter du code à un rapport &#40;SSRS&#41;](../../reporting-services/report-design/add-code-to-a-report-ssrs.md).  
  
### Pour ajouter une référence d'assembly à un rapport  
  
1.  En mode **Conception**, cliquez avec le bouton droit sur l’aire de conception à l’extérieur de la bordure du rapport et cliquez sur **Propriétés du rapport**.  
  
2.  Cliquez sur **Références**.  
  
3.  Dans **Ajouter ou supprimer des assemblys**, cliquez sur **Ajouter**, puis sur le bouton de sélection pour accéder à l’assembly.  
  
4.  Dans **Ajouter ou supprimer des classes**, cliquez sur **Ajouter**, puis tapez le nom de la classe et fournissez le nom d’une instance à utiliser dans le rapport.  
  
    > [!NOTE]  
    >  Spécifiez une classe et un nom d'instance uniquement pour les membres basés sur une instance. Ne spécifiez pas de membres statiques dans la liste **Classes**. Pour plus d’informations, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Utilisation d'assemblys personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Boîte de dialogue Propriétés du rapport, Références](../Topic/Report%20Properties%20Dialog%20Box,%20References.md)  
  
  