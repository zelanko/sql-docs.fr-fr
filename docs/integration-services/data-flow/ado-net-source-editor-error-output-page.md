---
title: "Éditeur de Source ADO NET (Page sortie d’erreur) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7889b092dae9abe613b3c4b2fe8d18500dea69f0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="ado-net-source-editor-error-output-page"></a>Éditeur de source ADO NET (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de source ADO NET** pour sélectionner les options de gestion des erreurs et pour définir les propriétés des colonnes de sortie d'erreur.  
  
 Pour en savoir plus sur la source ADO NET, consultez [ADO NET Source](../../integration-services/data-flow/ado-net-source.md).  
  
 **Pour ouvrir la page Sortie d'erreur**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui possède la source ADO NET.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source ADO NET.  
  
3.  Dans l' **Éditeur de source ADO NET**, cliquez sur **Sortie d'erreur**.  
  
## <a name="options"></a>Options  
 **Entrée/sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Affichez les colonnes externes (sources) que vous avez sélectionnées dans la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source ADO NET** .  
  
 **Erreur**  
 Indiquez ce qui doit se produire lorsqu'une erreur se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Rubriques connexes :** [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **Troncation**  
 Indiquez ce qui doit se produire lorsqu'une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Affiche la description de l'erreur.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Indiquez ce qui doit se produire pour l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source ADO NET &#40; Page Gestionnaire de connexions &#41;](../../integration-services/data-flow/ado-net-source-editor-connection-manager-page.md)   
 [Éditeur de Source ADO NET &#40; Page colonnes &#41;](../../integration-services/data-flow/ado-net-source-editor-columns-page.md)   
 [Gestionnaire de connexions ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  
