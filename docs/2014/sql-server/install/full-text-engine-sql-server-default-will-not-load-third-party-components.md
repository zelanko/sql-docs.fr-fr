---
title: Le moteur de recherche en texte intégral Microsoft pour SQL Server ne chargera pas par défaut les composants tiers non signés | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12ff188fb6aa6ac286817a7cc1c3ad726483c886
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012476"
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
  
  
