---
title: Les répertoires virtuels ne sont pas spécifiés (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c9ee7f745fc683a9ed93f2ca09ac94e1bf580f71
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952378"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>Les répertoires virtuels ne sont pas spécifiés (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau n'a pas détecté de paramètres de répertoire virtuel pour le service Web Report Server ou le Gestionnaire de rapports. Une fois la mise à niveau terminée, vous devez configurer des réservations d'URL pour le serveur de rapports à l'aide du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode natif.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Lors de la mise à niveau d'une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de nouvelles URL sont réservées pour le service Web Report Server et le Gestionnaire de rapports. Le Conseiller de mise à niveau n'a détecté aucun répertoire virtuel pour le serveur de rapports ou le Gestionnaire de rapports dans l'instance à mettre à niveau ; par conséquent, le processus de mise à niveau ne dispose pas d'informations suffisantes pour créer des réservations d'URL pour le serveur de rapports mis à niveau. La mise à niveau peut continuer, mais le répertoire virtuel du serveur de rapports ou du Gestionnaire de rapports ne sera pas défini après l'installation mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Une fois la mise à niveau terminée, utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour définir les URL pour le serveur de rapports et le Gestionnaire de rapports. Utilisez le gestionnaire des services Internet pour supprimer tous les répertoires virtuels dont vous n’avez plus besoin.  
  
 Pour plus d’informations, consultez [configurer une URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Reporting Services &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
