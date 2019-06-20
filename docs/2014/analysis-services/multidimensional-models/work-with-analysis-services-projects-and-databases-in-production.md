---
title: Utilisation Analysis Services projets et bases de données dans un environnement de Production | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: c589097f-ad29-4b97-8c7e-b8a910909c1a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f46a518acb4ba647b5b7bf5503ef76af7b6b90d8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66072429"
---
# <a name="working-with-analysis-services-projects-and-databases-in-a-production-environment"></a>Utilisation de projets et de bases de données Analysis Services dans un environnement de production
  Après avoir développé et déployé une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans une instance d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous devez décider de la façon dont vous souhaitez modifier les objets dans la base de données déployée. Certaines modifications, telles que celles associées aux rôles de sécurité, au partitionnement et aux paramètres de stockage, peuvent être effectuées à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. D’autres modifications peuvent être effectuées uniquement en utilisant [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en mode projet ou en mode en ligne (comme ajouter des attributs ou des hiérarchies définies par l’utilisateur).  
  
 Dès que vous apportez une modification à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployée à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode en ligne, le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui a été utilisé pour le déploiement devient obsolète. Si un développeur modifie le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et déploie le projet modifié, un message l'invitera à remplacer la totalité de la base de données. S'il remplace la base de données, cette dernière doit également être traitée. Le problème devient complexe si les modifications effectuées directement dans la base de données déployée par l’équipe de production n’ont pas été communiquées à l’équipe de développement, car cette dernière ne comprendra pas pourquoi ses modifications n’apparaissent plus dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Vous disposez de plusieurs méthodes vous permettant d'utiliser les outils SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour éviter les problèmes inhérents à cette situation.  
  
-   Méthode 1 : Si une modification est apportée à une version de production une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de base de données, utilisez [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour créer un nouveau [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet basé sur la version modifiée de la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données. Ce nouveau projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut être archivé dans le système de contrôle du code source comme copie principale du projet. Cette méthode fonctionne indépendamment du fait que les modifications ont été effectuées dans la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode en ligne.  
  
-   Méthode 2 : Modifiez uniquement la version de production une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l’aide de la base de données [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode projet. Cette méthode vous permet d’utiliser les options disponibles dans l’Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour conserver les modifications effectuées par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], notamment les rôles de sécurité et les paramètres de stockage. Les paramètres liés à la conception sont donc conservés dans le fichier de projet (les paramètres de stockage et les rôles de sécurité peuvent être ignorés) et le serveur en ligne est utilisé pour les paramètres de stockage et les rôles de sécurité.  
  
-   Méthode 3 : Modifiez uniquement la version de production une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l’aide de la base de données [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en mode en ligne. Étant donné que les deux outils fonctionnent sur le même serveur en ligne, la version sera synchronisée.  
  
  
