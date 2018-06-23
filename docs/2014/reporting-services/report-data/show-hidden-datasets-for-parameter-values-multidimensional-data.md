---
title: Afficher des Datasets masqués pour les valeurs de paramètre pour les données multidimensionnelles (Générateur de rapports et SSRS) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 89df13eecdce33869199e0b5a8e82b0395679475
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041970"
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
 [Ajouter des données à un rapport &#40;rapport Générateur et SSRS&#41;](report-datasets-ssrs.md)  
  
  