---
title: Propriétés de SQL Server Agent (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 66a7b7cd9328f70e5b5ca374a04ad5e9dd6e079a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63245779"
---
# <a name="sql-server-agent-properties-general-page"></a>Propriétés de SQL Server Agent (page Général)
  Utilisez cette page pour afficher et modifier les propriétés générales du service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
 **État du service**  
 Affiche l'état actuel du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Redémarrage automatique de SQL Server après un arrêt inattendu**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent redémarre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cas d’arrêt inattendu de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Redémarrage automatique de l'Agent SQL Server après un arrêt inattendu**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] redémarre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent en cas d’arrêt inattendu de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Nom du fichier**  
 Spécifiez le nom de fichier du journal des erreurs.  
  
 **...**  
 Permet de parcourir l'arborescence à la recherche du fichier journal des erreurs.  
  
 **Inclure les messages de trace d'exécution**  
 Inclut des messages de trace d'exécution dans le journal des erreurs. Les messages de trace fournissent des informations détaillées sur le fonctionnement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Le fichier journal nécessite donc davantage d'espace disque lorsque cette option est activée. Vous ne devez activer cette option que pour résoudre un problème susceptible d'impliquer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Enregistrer le fichier OEM**  
 Écrit le fichier journal des erreurs comme un fichier non-Unicode. Cela réduit l'espace disque utilisé par le fichier journal. Toutefois, si vous activez cette option, sachez que les messages incluant des données Unicode peuvent être plus difficiles à lire.  
  
 **Destinataire d'envoi réseau**  
 Tapez le nom d'un opérateur destiné à recevoir la notification envoyée par réseau des messages que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent consigne dans le fichier journal.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs](operators.md)   
 [Journal des erreurs de l'Agent SQL Server](sql-server-agent-error-log.md)  
  
  
