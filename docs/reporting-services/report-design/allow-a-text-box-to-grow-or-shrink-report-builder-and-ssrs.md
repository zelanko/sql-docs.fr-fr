---
title: "Autoriser une zone de texte s’agrandissent ou réduisent (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbc01e78-5993-47e5-af04-34f9e3bbcee1
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: abb928e42a7420b421c91f6b5f78256213cb5df9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs"></a>Autoriser l'agrandissement ou la réduction d'une zone de texte (Générateur de rapports et SSRS)
  Dans un rapport paginé [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , les zones de texte ne se limitent pas aux zones autonomes situées sur l’aire de conception. Chaque cellule d’une table ou d’une matrice (région de données de tableau matriciel) contient également une zone de texte, que vous pouvez mettre en forme de la même manière que les zones de texte autonomes. Par défaut, les zones de texte ont une taille fixe. Vous pouvez définir les options qui autorisent la réduction ou l’agrandissement de la zone de texte en fonction de son contenu. Ces options correspondent aux propriétés **CanGrow** ou **CanShrink** du volet Propriétés.  
  
## <a name="to-allow-a-text-box-to-grow-or-shrink"></a>Pour autoriser l'agrandissement ou la réduction d'une zone de texte  
  
1.  Cliquez avec le bouton droit sur la zone de texte, puis cliquez sur **Propriétés de la zone de texte**.  
  
2.  Cliquez sur l'onglet **Général** .  
  
    -   Si vous souhaitez autoriser l'agrandissement vertical de la zone de texte en fonction de son contenu, sélectionnez **Autoriser l'augmentation de la hauteur**.  
  
    -   Si vous souhaitez autoriser la réduction de la zone de texte en fonction de son contenu, sélectionnez **Autoriser la réduction de la hauteur**.  
  
## <a name="see-also"></a>Voir aussi  
 [Zones de texte &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)  
  
  
