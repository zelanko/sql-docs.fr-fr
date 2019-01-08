---
title: Les modèles tabulaires dans Analysis Services | Microsoft Docs
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae7dfd78e71c41ab5b826a27742923445117417d
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072036"
---
# <a name="tabular-models"></a>Modèles tabulaires
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Les modèles tabulaires dans Analysis Services sont des bases de données qui s’exécutent en mémoire ou en mode DirectQuery, connexion aux données directement à partir de données relationnelles back-end sources. En utilisant des algorithmes de compression de pointe et processeur de requêtes multithread, le moteur analytique Vertipaq Analysis Services permet un accès rapide aux objets de modèle tabulaire et aux données par des applications clientes comme Power BI et Excel.  
  
 Tandis que les modèles en mémoire sont la valeur par défaut, DirectQuery est un mode de requête alternatif pour les modèles qui sont trop volumineuses pour tenir en mémoire, ou la volatilité des données empêche une stratégie de traitement raisonnable. DirectQuery permet d’obtenir une parité avec les modèles en mémoire via la prise en charge pour un large éventail de sources de données, capacité à gérer des tables calculées et colonnes dans un modèle DirectQuery, la sécurité au niveau des lignes via des expressions DAX qui atteignent la base de données back-end et de requête optimisations qui entraînent un débit plus rapide.
  
 Les modèles tabulaires sont créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] à l’aide du modèle de projet de modèle tabulaire. Le modèle de projet fournit une aire de conception pour créer des objets de modèle sémantique, comme les tables, les partitions, les relations, les hiérarchies, les mesures et les indicateurs de performance clés. 
  
 Modèles tabulaires peuvent être déployés sur Azure Analysis Services ou une instance de SQL Server Analysis Services est configuré pour le mode serveur tabulaire. Les modèles tabulaires déployés peuvent être gérés dans SQL Server Management Studio. 

Documentation de modélisation tabulaire incluse dans cette rubrique s’applique, dans la plupart des cas, SQL Server Analysis Services et Azure Analysis Services. Articles ayant trait à Azure Analysis Services sont publiés, ainsi que d’autres documentations Azure. Pour plus d’informations, consultez [documentation Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).
  
