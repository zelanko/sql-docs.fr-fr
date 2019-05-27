---
title: Restriction d’adresse IP détectée (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ec72f58aaa0a10d0fa13860bc39e81b717d0ff89
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094181"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>Restriction par adresse IP détectée (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté une ou plusieurs restrictions par adresse IP sur le site Web IIS qui héberge les répertoires virtuels du serveur de rapports ou du Gestionnaire de rapports. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne fournit pas de prise en charge native pour les restrictions par adresse IP.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le programme d'installation ne peut pas définir de restrictions par adresse IP sur des URL créées pour un serveur de rapports mis à niveau. La mise à niveau peut continuer, mais les restrictions par adresse IP ne seront pas définies sur les URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Après la mise à niveau, utilisez ISA Server, votre logiciel de pare-feu ou toute autre solution pour autoriser ou exclure les requêtes émanant d'adresses IP spécifiques et destinées au serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
