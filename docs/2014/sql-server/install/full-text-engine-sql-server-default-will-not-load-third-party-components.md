---
title: Le moteur de recherche en texte intégral Microsoft pour SQL Server ne chargera pas les composants tiers non signés par défaut | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b6c3adecfac495a72a86b093113c67d19bb9e7e0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244219"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>Le service MSFTESQL (Microsoft Full-Text Engine for SQL Server) ne chargera pas par défaut les composants tiers non signés
  Par défaut, le service MSFTESQL ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) ne charge pas les composants qui ne sont pas signés par [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="component"></a>Composant  
 Recherche en texte intégral  
  
## <a name="description"></a>Description  
 Un filtre d'un fournisseur tiers, par exemple un filtre PDF déjà installé sur le serveur, n'est pas chargé par le service MSFTESQL ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) par défaut après la mise à niveau.  
  
## <a name="corrective-action"></a>Action corrective  
 Pour charger un filtre tiers, vous devez définir *load_os_resource* et désactiver *verify_signature* sur cette instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
