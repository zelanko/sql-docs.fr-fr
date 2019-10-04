---
title: Certificats clients sur le site Web du serveur de rapports (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5588930efbadf785e78aa115ad0021bce64bd7f7
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952600"
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
 [Conseiller de mise &#40;à niveau des problèmes de mise à niveau Reporting Services&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
