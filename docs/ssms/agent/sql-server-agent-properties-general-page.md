---
description: Propriétés de SQL Server Agent (page Général)
title: Propriétés de SQL Server Agent (page Général)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f08f8fe21876f5a04e817c367ece49d44eef93c5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88370915"
---
# <a name="sql-server-agent-properties-general-page"></a>Propriétés de SQL Server Agent (page Général)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et modifier les propriétés générales du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
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
[Opérateurs](../../ssms/agent/operators.md)  
[Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
