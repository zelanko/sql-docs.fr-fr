---
title: "Déployer des projets Analysis Services (SSDT) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dbfe19ac5da2fee064dd19d06aa1bf7992c3429b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="deploy-analysis-services-projects-ssdt"></a>Déployer des projets Analysis Services (SSDT)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Pendant le développement d’un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous déployez fréquemment le projet sur un serveur de développement afin de créer le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] définie par le projet de base de données. Cette opération est nécessaire pour tester le projet ; par exemple, pour explorer les cellules d'un cube, explorer les membres de dimension ou vérifier les formules des indicateurs de performances clés (KPI).  
  
## <a name="deploying-a-project"></a>Déploiement d'un projet  
 Vous pouvez déployer un projet indépendamment des autres ou déployer tous les projets d'une solution. Lorsque vous déployez un projet, plusieurs étapes se succèdent. Tout d'abord, le projet est généré. Cette étape crée les fichiers de sortie qui définissent la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et les objets qui la constituent. Ensuite, le serveur de destination est validé. Et pour finir, la base de données de destination et ses objets sont créés sur le serveur de destination. Pendant le déploiement, le moteur de déploiement remplace le contenu des bases de données préexistantes par le contenu du projet sauf si ces objets ont été créés par le projet au cours d'un déploiement précédent.  
  
 Après un déploiement initial, un fichier IncrementalSnapshot.xml est généré dans le \<nom du projet > \obj dossier. Ce fichier permet de déterminer si la base de données ou ses objets sur le serveur de destination ont été modifiés hors du projet. Dans l'affirmative, vous serez invité à remplacer tous les objets dans la base de données de destination. Si toutes les modifications ont été apportées dans le projet et que le projet est configuré en vue d'un déploiement incrémentiel, seules les modifications seront déployées sur le serveur de destination.  
  
 La configuration du projet et ses paramètres associés déterminent les propriétés de déploiement qui seront utilisées pour déployer le projet. Pour un projet partagé, chaque développeur peut utiliser sa propre configuration avec ses propres options de configuration du projet. Par exemple, chaque développeur peut spécifier un serveur de test différent pour travailler isolément des autres développeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un projet Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
