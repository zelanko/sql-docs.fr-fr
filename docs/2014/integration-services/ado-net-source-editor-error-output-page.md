---
title: Éditeur de Source ADO NET (Page sortie d’erreur) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b47f60480938467fb8e618a0fa52b91449fafa54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053571"
---
# <a name="ado-net-source-editor-error-output-page"></a>Éditeur de source ADO NET (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de source ADO NET** pour sélectionner les options de gestion des erreurs et pour définir les propriétés des colonnes de sortie d'erreur.  
  
 Pour en savoir plus sur la source ADO NET, consultez [ADO NET Source](data-flow/ado-net-source.md).  
  
 **Pour ouvrir la page Sortie d'erreur**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui possède la source ADO NET.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source ADO NET.  
  
3.  Dans l' **Éditeur de source ADO NET**, cliquez sur **Sortie d'erreur**.  
  
## <a name="options"></a>Options  
 **Entrée/sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Affichez les colonnes externes (sources) que vous avez sélectionnées dans la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source ADO NET** .  
  
 **Erreur**  
 Indiquez ce qui doit se produire lorsqu'une erreur se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Rubriques connexes :** [Gestion des erreurs dans les données](data-flow/error-handling-in-data.md)  
  
 **Troncation**  
 Indiquez ce qui doit se produire lorsqu'une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Affiche la description de l'erreur.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Indiquez ce qui doit se produire pour l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source ADO NET &#40;Page Gestionnaire de connexions&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md)   
 [Éditeur de Source ADO NET &#40;Page colonnes&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md)   
 [Gestionnaire de connexions ADO.NET](connection-manager/ado-net-connection-manager.md)  
  
  