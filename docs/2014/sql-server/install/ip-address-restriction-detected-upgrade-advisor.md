---
title: Restriction d’adresse IP détectée (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 487ced9f103fd10a581841595111f01a5710bd15
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952082"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>Restriction par adresse IP détectée (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté une ou plusieurs restrictions par adresse IP sur le site Web IIS qui héberge les répertoires virtuels du serveur de rapports ou du Gestionnaire de rapports. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne fournit pas de prise en charge native pour les restrictions par adresse IP.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] natif.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Le programme d'installation ne peut pas définir de restrictions par adresse IP sur des URL créées pour un serveur de rapports mis à niveau. La mise à niveau peut continuer, mais les restrictions par adresse IP ne seront pas définies sur les URL de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Après la mise à niveau, utilisez ISA Server, votre logiciel de pare-feu ou toute autre solution pour autoriser ou exclure les requêtes émanant d'adresses IP spécifiques et destinées au serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseiller de mise &#40;à niveau des problèmes de mise à niveau Reporting Services&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
