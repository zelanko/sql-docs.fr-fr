---
title: Compatibilité descendante IIS composants n’ont pas étés détecté (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9cfae4d34ef825ac1781c90fda8d7e38c0299a1b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094781"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>Les composants de compatibilité descendante IIS n'ont pas été détectés (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau n'a pas détecté les composants et paramètres IIS qui fournissent des informations utilisées par le programme d'installation pour créer les nouvelles URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 IIS inclut des composants qui fournissent des informations sur les répertoires virtuels du serveur de rapports et du Gestionnaire de rapports, et ces composants ne sont pas installés sur l'ordinateur serveur de rapports. La mise à niveau peut continuer, mais les URL du serveur de rapports et du Gestionnaire de rapports ne seront pas recréées par la mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Une fois la mise à niveau terminée, utilisez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour définir les URL pour le serveur de rapports ou le Gestionnaire de rapports. Utilisez le Gestionnaire des services IIS pour supprimer les répertoires virtuels dont vous n'avez plus besoin.  
  
 Pour plus d’informations, consultez [configurer une URL &#40;Gestionnaire de Configuration de SSRS&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
