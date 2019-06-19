---
title: Configurer les journaux d’erreurs de SQL Server Agent (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 96d0105faad9fb4c2c3213eaa90da464ccd90bd6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63253883"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>Configurer les journaux d’erreurs de SQL Server Agent (page Général)
  Utilisez cet écran pour afficher et mettre à jour les paramètres du journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
 **Fichier journal des erreurs**  
 Spécifie le nom du fichier dans lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent consigne les erreurs.  
  
 **...**  
 Permet de parcourir l'arborescence à la recherche du fichier journal des erreurs.  
  
 **Écrire dans le fichier journal des erreurs OEM**  
 Écrit le fichier journal des erreurs comme un fichier non-Unicode. Cela réduit l'espace disque utilisé par le fichier journal. Toutefois, si vous activez cette option, sachez que les messages incluant des données Unicode peuvent être plus difficiles à lire.  
  
 **Erreurs**  
 Écrit uniquement les erreurs et les messages d'information dans le fichier journal.  
  
 **Avertissements**  
 Écrit uniquement les avertissements et les messages d'information dans le fichier journal.  
  
 **Informations**  
 Écrit uniquement les messages d'information dans le fichier journal.  
  
## <a name="see-also"></a>Voir aussi  
 [Journal des erreurs de l'Agent SQL Server](sql-server-agent-error-log.md)  
  
  
