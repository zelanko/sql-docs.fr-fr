---
title: Domaines d’application et de sécurité de l’intégration CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3f2ff171562929a035cb80fed556c954508c5557
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62753771"
---
# <a name="application-domains-and-clr-integration-security"></a>Domaines d'application et sécurité de l'intégration du CLR
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge des assemblys qui appartiennent au même propriétaire dans le même domaine d'application. En raison d'un jeu d'assemblys s'exécutant dans le même domaine d'application, les assemblys sont capables de se découvrir les uns les autres au moment de l'exécution à l'aide d'interfaces de programmation d'applications de réflexion du .NET Framework ou par d'autres moyens, et ils sont capables d'y faire des appels en mode de liaison tardive. De tels appels se produisant sur des assemblys qui appartiennent au même propriétaire, aucune autorisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est vérifiée pour ces appels. Le schéma de positionnement des assemblys dans les domaines d'application est principalement conçu pour répondre à des objectifs en matière d'évolutivité, de sécurité et d'isolation. Il est susceptible d'être modifié dans des versions ultérieures. Pour cette raison, il est possible que la recherche d'assemblys dans le même domaine d'application par le biais de mécanismes à liaison tardive s'avère infructueuse.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’intégration du CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
