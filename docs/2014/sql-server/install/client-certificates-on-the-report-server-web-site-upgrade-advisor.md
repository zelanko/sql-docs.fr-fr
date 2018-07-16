---
title: Certificats clients sur le site web serveur de rapports (Conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 93128f60320fbcf82a3368d6008fe647497fa4dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270285"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>Certificats clients sur le site Web du serveur de rapports (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté un ou plusieurs certificats clients sur le site Web IIS qui héberge les répertoires virtuels du serveur de rapports ou du Gestionnaire de rapports.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prend pas en charge l'utilisation de certificats clients pour authentifier des utilisateurs. La mise à niveau peut se poursuivre, mais les certificats clients ne seront pas utilisés par le serveur de rapports mis à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Vous devrez recourir à une solution distincte, par exemple ISA Server, pour garantir que toutes les exigences d'authentification des certificats clients seront satisfaites.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Reporting Services &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
