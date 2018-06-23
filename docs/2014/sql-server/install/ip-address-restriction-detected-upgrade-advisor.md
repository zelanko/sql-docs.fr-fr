---
title: Restriction d’adresse IP détectée (Conseiller de mise à niveau) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: b3ab784e15737a08b9bf928d6d15e08a27636b88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043747"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>Restriction par adresse IP détectée (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté une ou plusieurs restrictions par adresse IP sur le site Web IIS qui héberge les répertoires virtuels du serveur de rapports ou du Gestionnaire de rapports. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne fournit pas de prise en charge native pour les restrictions par adresse IP.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Natif.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le programme d'installation ne peut pas définir de restrictions par adresse IP sur des URL créées pour un serveur de rapports mis à niveau. La mise à niveau peut continuer, mais les restrictions par adresse IP ne seront pas définies sur les URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Après la mise à niveau, utilisez ISA Server, votre logiciel de pare-feu ou toute autre solution pour autoriser ou exclure les requêtes émanant d'adresses IP spécifiques et destinées au serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;le Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  