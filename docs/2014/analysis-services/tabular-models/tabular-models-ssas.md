---
title: Tabulaire (SSAS tabulaire) de modélisation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 11a5a9332c7fa85fd6407523ffd9c7c48a2c0514
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198749"
---
# <a name="tabular-modeling-ssas-tabular"></a>Modélisation tabulaire (SSAS Tabulaire)
  Les modèles tabulaires sont des bases de données en mémoire dans Analysis Services. À l'aide d'algorithmes de compression de pointe et du processeur de requêtes multithread, le moteur d'analyse en mémoire xVelocity (VertiPaq) permet un accès rapide aux objets de modèles tabulaires et aux données par les applications clientes de création de rapports telles que Microsoft Excel et Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
 Les modèles tabulaires prennent en charge l'accès aux données selon deux modes : mode mis en cache et mode DirectQuery. En mode mis en cache, vous pouvez intégrer des données de plusieurs sources, notamment des bases de données relationnelles, des flux de données et des fichiers texte en deux dimensions. En mode DirectQuery, vous pouvez ignorer le modèle en mémoire, ce qui permet aux applications clientes d'interroger des données directement au niveau de la source (SQL Server relationnel).  
  
 Les modèles tabulaires sont créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] à l'aide de nouveaux modèles de projet de modèles tabulaires. Vous pouvez importer des données depuis plusieurs sources, puis enrichir le modèle en ajoutant des relations, des colonnes calculées, des mesures, des indicateurs de performance clés et des hiérarchies. Des modèles peuvent ensuite être déployés sur une instance d'Analysis Services à laquelle les applications clientes de création de rapports peuvent se connecter. Les modèles déployés peuvent être gérés dans SQL Server Management Studio comme tous les modèles multidimensionnels. Ils peuvent également être partitionnés pour un traitement optimisé et être sécurisés au niveau de la ligne à l'aide de la sécurité basée sur le rôle.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Solutions de modèles tabulaires &#40;SSAS tabulaire&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
 [Bases de données Model tabulaire &#40;SSAS tabulaire&#41;](tabular-model-databases-ssas-tabular.md)  
  
 [Accès aux données de modèle tabulaire](tabular-model-data-access.md)  
  
  
