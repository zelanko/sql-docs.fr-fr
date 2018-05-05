---
title: Les modèles tabulaires | Documents Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2886f357fc93b1ae39197c7624cac88b2bc18837
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="tabular-models"></a>Modèles tabulaires
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Les modèles tabulaires sont des bases de données Analysis Services qui s’exécutent en mémoire ou en mode DirectQuery, en accédant aux données directement à partir de sources de données relationnelles principales. À l’aide des algorithmes de compression de pointe et processeur de requêtes multithread, le moteur analytique permet un accès rapide aux données et objets de modèle tabulaire en utilisant des applications clientes telles que Power BI et Excel.  
  
 Alors que les modèles en mémoire sont la valeur par défaut, DirectQuery est un mode de requête alternatif pour les modèles qui sont trop volumineux pour tenir en mémoire, ou lorsque la volatilité des données empêche une stratégie de traitement raisonnable. DirectQuery permet d’obtenir la parité avec les modèles en mémoire prise en charge pour un large éventail de sources de données, permet de gérer les tables calculées et les colonnes dans un modèle DirectQuery, la sécurité de niveau ligne via des expressions DAX qui atteignent la base de données et de requête optimisations qui entraînent un débit plus rapide.
  
 Les modèles tabulaires sont créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] à l’aide du modèle de projet de modèle tabulaire qui fournit une aire de conception pour la création d’un modèle, les tables, les relations et les expressions DAX. Vous pouvez importer des données depuis plusieurs sources, puis enrichir le modèle en ajoutant des relations, des colonnes et des tables calculées, des mesures, des indicateurs de performance clés, des hiérarchies et des traductions.  
  
 Les modèles peuvent ensuite être déployés sur Azure Analysis Services ou une instance de SQL Server Analysis Services est configuré pour le mode serveur tabulaire. Les modèles tabulaires déployés peuvent être gérés dans SQL Server Management Studio. À mesure que vos modèles augmentent, ils peuvent partitionnés pour un traitement optimisé et sécurisées au niveau de la ligne à l’aide en fonction du rôle de sécurité.  

  
  
