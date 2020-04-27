---
title: Déployer des projets Analysis Services (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5b6c79c2ea4355e9d889e235c8185a2460c0ed8c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075388"
---
# <a name="deploy-analysis-services-projects-ssdt"></a>Déployer des projets Analysis Services (SSDT)
  En phase de développement d’un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous déployez fréquemment le projet sur un serveur de déploiement pour créer la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] définie par le projet. Cette opération est nécessaire pour tester le projet ; par exemple, pour explorer les cellules d'un cube, explorer les membres de dimension ou vérifier les formules des indicateurs de performances clés (KPI).  
  
## <a name="deploying-a-project"></a>Déploiement d'un projet  
 Vous pouvez déployer un projet indépendamment des autres ou déployer tous les projets d'une solution. Lorsque vous déployez un projet, plusieurs étapes se succèdent. Tout d'abord, le projet est généré. Cette étape crée les fichiers de sortie qui définissent la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et les objets qui la constituent. Ensuite, le serveur de destination est validé. Et pour finir, la base de données de destination et ses objets sont créés sur le serveur de destination. Pendant le déploiement, le moteur de déploiement remplace le contenu des bases de données préexistantes par le contenu du projet sauf si ces objets ont été créés par le projet au cours d'un déploiement précédent.  
  
 Après un déploiement initial, un fichier IncrementalSnapshot. xml est généré dans le \<nom du projet> dossier \obj. Ce fichier permet de déterminer si la base de données ou ses objets sur le serveur de destination ont été modifiés hors du projet. Dans l'affirmative, vous serez invité à remplacer tous les objets dans la base de données de destination. Si toutes les modifications ont été apportées dans le projet et que le projet est configuré en vue d'un déploiement incrémentiel, seules les modifications seront déployées sur le serveur de destination.  
  
 La configuration du projet et ses paramètres associés déterminent les propriétés de déploiement qui seront utilisées pour déployer le projet. Pour un projet partagé, chaque développeur peut utiliser sa propre configuration avec ses propres options de configuration du projet. Par exemple, chaque développeur peut spécifier un serveur de test différent pour travailler isolément des autres développeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un projet Analysis Services &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)  
  
  
