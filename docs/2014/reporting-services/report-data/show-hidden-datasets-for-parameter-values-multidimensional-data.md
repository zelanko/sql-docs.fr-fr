---
title: Afficher des Datasets masqués pour les valeurs de paramètre des données multidimensionnelles (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 50da5a57968a7304c206f2aceb2efc24239600b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224679"
---
# <a name="show-hidden-datasets-for-parameter-values-for-multidimensional-data-report-builder-and-ssrs"></a>Afficher des datasets masqués pour les valeurs de paramètres des données multidimensionnelles (Générateur de rapports et SSRS)
  Votre rapport peut inclure des datasets générés automatiquement (aussi appelés datasets masqués) qui n'apparaissent pas par défaut dans le volet des données de rapport. La création de ces datasets s'effectue de plusieurs façons :  
  
-   Dans certains concepteurs de requêtes pour des bases de données multidimensionnelles, vous pouvez spécifier des champs sur lesquels appliquer un filtre dans la zone de filtre du volet de requête, et indiquer si vous voulez ou non créer un paramètre de requête pour le filtre. Si vous sélectionnez l'option de paramètre, des datasets de rapport sont automatiquement créés pour fournir des valeurs valides pour le paramètre de rapport.  
  
-   Si vous importez une requête basée sur des bases de données multidimensionnelles, vous pouvez également inclure des datasets masqués dans votre rapport.  
  
 Les datasets masqués ne sont pas accessibles à partir d'un Assistant.  
  
 Vous pouvez modifier la vue dans le volet des données de rapport pour afficher tous les datasets dans le rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a>Pour afficher les datasets masqués  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur le dossier Datasets, puis cliquez sur **Afficher les datasets masqués**.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../query-designers-report-builder.md)   
 [Concepteurs de requêtes Reporting Services](../reporting-services-query-designers.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)  
  
  
