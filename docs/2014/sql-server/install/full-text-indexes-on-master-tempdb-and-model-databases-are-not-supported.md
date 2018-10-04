---
title: Index de recherche en texte intégral sur les bases de données master, tempdb et model ne sont pas prises en charge | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f055640dbdbf4ece491b2d8552c1581b122faed3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064909"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Les index de recherche en texte intégral ne sont pas pris en charge dans les bases de données master, tempdb et model
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne permet pas de créer des index de recherche en texte intégral sur une base de données système.  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], les index de texte intégral étaient pris en charge sur les bases de données master, tempdb et model.  
  
 Tous les catalogues de texte intégral dans master, tempdb et bases de données model sont supprimés pendant la mise à niveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
