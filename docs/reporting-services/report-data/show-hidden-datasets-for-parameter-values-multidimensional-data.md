---
title: Afficher des datasets masqués pour les valeurs de paramètres - Données multidimensionnelles | Microsoft Docs
description: Découvrez comment afficher les jeux de données masqués pour les valeurs de paramètres afin de pouvoir afficher tous les jeux de données dans un rapport.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4118c7ad1cccb46a08ec200eef223f62010cf45e
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91890818"
---
# <a name="show-hidden-datasets-for-parameter-values---multidimensional-data"></a>Afficher des datasets masqués pour les valeurs de paramètres - Données multidimensionnelles
  Votre rapport peut inclure des datasets générés automatiquement (aussi appelés datasets masqués) qui n'apparaissent pas par défaut dans le volet des données de rapport. La création de ces datasets s'effectue de plusieurs façons :  
  
-   Dans certains concepteurs de requêtes pour des bases de données multidimensionnelles, vous pouvez spécifier des champs sur lesquels appliquer un filtre dans la zone de filtre du volet de requête, et indiquer si vous voulez ou non créer un paramètre de requête pour le filtre. Si vous sélectionnez l'option de paramètre, des datasets de rapport sont automatiquement créés pour fournir des valeurs valides pour le paramètre de rapport.  
  
-   Si vous importez une requête basée sur des bases de données multidimensionnelles, vous pouvez également inclure des datasets masqués dans votre rapport.  
  
 Les datasets masqués ne sont pas accessibles à partir d'un Assistant.  
  
 Vous pouvez modifier la vue dans le volet des données de rapport pour afficher tous les datasets dans le rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a>Pour afficher les datasets masqués  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur le dossier Datasets, puis cliquez sur **Afficher les datasets masqués**.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de création de requêtes &#40;SSRS&#41;](query-design-tools-ssrs.md)   
 [Concepteurs de requêtes Reporting Services](/previous-versions/sql/)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Datasets de rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
  
