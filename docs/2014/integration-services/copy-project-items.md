---
title: Copier des éléments de projet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4185751f0aded344577acb6206f259debdb37642
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374118"
---
# <a name="copy-project-items"></a>Copier des éléments de projet
  Cette rubrique explique comment copier des objets dans un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou entre des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Vous pouvez également copier des objets entre les autres types de projets [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour pouvoir effectuer une copie entre des projets, il faut qu'ils appartiennent à la même solution [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Projets Integration Services &#40;SSIS&#41;](integration-services-ssis-projects-and-solutions.md).  
  
### <a name="to-copy-project-level-items"></a>Pour copier des éléments de niveau projet  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet ou la solution [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] avec lequel vous voulez travailler.  
  
2.  Développez le projet et le dossier de l'élément à partir desquels effectuer la copie.  
  
3.  Cliquez avec le bouton droit sur l’élément, puis cliquez sur **Copier**.  
  
4.  Cliquez avec le bouton droit sur le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vers lequel effectuer la copie, puis cliquez sur **Coller**.  
  
     Les éléments sont automatiquement copiés dans le dossier approprié. Si vous copiez dans le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] des éléments qui ne sont pas des packages, ces éléments sont copiés dans le dossier **Divers**.  
  
## <a name="see-also"></a>Voir aussi  
 [Packages Integration Services &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Copier des objets de packages](../../2014/integration-services/copy-package-objects.md)  
  
  
