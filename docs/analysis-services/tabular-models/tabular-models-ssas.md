---
title: Les modèles tabulaires | Microsoft Docs
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1f894ad30f6344eb832cb9549a60c7f60071188c
ms.sourcegitcommit: e34e9cd1b1ec02393dc88b1f0471023a7f7f278b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46506130"
---
# <a name="tabular-models"></a>Modèles tabulaires
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Les modèles tabulaires dans Analysis Services sont des bases de données qui s’exécutent en mémoire ou en mode DirectQuery, connexion aux données directement à partir de données relationnelles back-end sources. En utilisant des algorithmes de compression de pointe et processeur de requêtes multithread, le moteur analytique Vertipaq Analysis Services permet un accès rapide aux objets de modèle tabulaire et aux données par des applications clientes comme Power BI et Excel.  
  
 Tandis que les modèles en mémoire sont la valeur par défaut, DirectQuery est un mode de requête alternatif pour les modèles qui sont trop volumineuses pour tenir en mémoire, ou la volatilité des données empêche une stratégie de traitement raisonnable. DirectQuery permet d’obtenir une parité avec les modèles en mémoire via la prise en charge pour un large éventail de sources de données, capacité à gérer des tables calculées et colonnes dans un modèle DirectQuery, la sécurité au niveau des lignes via des expressions DAX qui atteignent la base de données back-end et de requête optimisations qui entraînent un débit plus rapide.
  
 Les modèles tabulaires sont créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] à l’aide du modèle de projet de modèle tabulaire. Le modèle de projet fournit une aire de conception pour créer des objets de modèle sémantique, comme les tables, les partitions, les relations, les hiérarchies, les mesures et les indicateurs de performance clés. 
  
 Modèles tabulaires peuvent être déployés sur Azure Analysis Services ou une instance de SQL Server Analysis Services est configuré pour le mode serveur tabulaire. Les modèles tabulaires déployés peuvent être gérés dans SQL Server Management Studio. 

Documentation de modélisation tabulaire incluse dans cette rubrique s’applique, dans la plupart des cas, SQL Server Analysis Services et Azure Analysis Services. Articles ayant trait à Azure Analysis Services sont publiés, ainsi que d’autres documentations Azure. Pour plus d’informations, consultez [documentation Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).
  
