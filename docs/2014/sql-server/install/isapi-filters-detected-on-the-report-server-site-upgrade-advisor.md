---
title: Filtres ISAPI détectés sur le site de serveur de rapports (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7b30b585fc0448f04be2ee98c23f53794675fefe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301433"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a>Des filtres ISAPI ont été détectés sur le site du serveur de rapports (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté un ou plusieurs filtres ISAPI sur le site Web qui héberge les répertoires virtuels du serveur de rapports et du Gestionnaire de rapports. Filtres ISAPI ne sont pas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Natif.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Avant la mise à niveau, vérifiez si les filtres ISAPI sur le site Web sont utilisés par les applications [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si vous n'avez pas besoin du filtre ISAPI, vous pouvez mettre à niveau le serveur de rapports. Le programme d'installation créera les URL par défaut, sans prise en charge pour le filtre ISAPI qui s'exécute dans IIS. Si vous avez besoin du filtre ISAPI, n'effectuez pas la mise à niveau tant que vous n'aurez pas trouvé une alternative pour héberger le filtre ISAPI (par exemple, utiliser ISA Server ou continuer à héberger le filtre ISAPI dans IIS). Le serveur de rapports prend en charge ASP.NET HTTPModules en remplacement des filtres ISAPI dans certains scénarios. Pour plus d'informations, consultez la documentation relative à ASP.NET sur MSDN.  
  
## <a name="corrective-action"></a>Action corrective  
 Évaluez et utilisez une solution distincte pour héberger les filtres ISAPI requis par votre déploiement.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
