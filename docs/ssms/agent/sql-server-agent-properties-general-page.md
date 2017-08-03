---
title: "Propriétés de SQL Server Agent (page Général) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4da1f93dcc4c6e75b554a1a6dab8cbeb86096009
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="sql-server-agent-properties-general-page"></a>Propriétés de SQL Server Agent (page Général)
Utilisez cette page pour afficher et modifier les propriétés générales du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Options  
**État du service**  
Affiche l'état actuel du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Redémarrage automatique de SQL Server après un arrêt inattendu**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent redémarre [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en cas d’arrêt inattendu de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Redémarrage automatique de l'Agent SQL Server après un arrêt inattendu**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] redémarre [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent en cas d’arrêt inattendu de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Nom du fichier**  
Spécifiez le nom de fichier du journal des erreurs.  
  
**...**  
Permet de parcourir l'arborescence à la recherche du fichier journal des erreurs.  
  
**Inclure les messages de trace d'exécution**  
Inclut des messages de trace d'exécution dans le journal des erreurs. Les messages de trace fournissent des informations détaillées sur le fonctionnement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Le fichier journal nécessite donc davantage d'espace disque lorsque cette option est activée. Vous ne devez activer cette option que pour résoudre un problème susceptible d'impliquer [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Enregistrer le fichier OEM**  
Écrit le fichier journal des erreurs comme un fichier non-Unicode. Cela réduit l'espace disque utilisé par le fichier journal. Toutefois, si vous activez cette option, sachez que les messages incluant des données Unicode peuvent être plus difficiles à lire.  
  
**Destinataire d'envoi réseau**  
Tapez le nom d'un opérateur destiné à recevoir la notification envoyée par réseau des messages que [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent consigne dans le fichier journal.  
  
## <a name="see-also"></a>Voir aussi  
[Opérateurs](../../ssms/agent/operators.md)  
[Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  

