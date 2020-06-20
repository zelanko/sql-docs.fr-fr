---
title: Les index de recherche en texte intégral sur les bases de données Master, tempdb et Model ne sont pas pris en charge | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fbd5e3133ed87fed9bdaf6d668df62c6471df766
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012463"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a>Les index de recherche en texte intégral ne sont pas pris en charge dans les bases de données master, tempdb et model
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne permet pas de créer des index de recherche en texte intégral sur une base de données système.  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], les index de texte intégral étaient pris en charge sur les bases de données master, tempdb et model.  
  
 Les catalogues de texte intégral dans les bases de données Master, tempdb et Model sont supprimés au cours de la mise à niveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
