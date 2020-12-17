---
description: Serveurs cibles (onglet État du serveur cible)
title: Serveurs cibles (onglet État du serveur cible)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.target.status.f1
ms.assetid: 010a4cab-d878-4889-8ac8-7d91db6345d6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 5767396a17a222ea0e90658eb7bc97171f0df409
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440410"
---
# <a name="target-servers-target-server-status-tab"></a>Serveurs cibles (onglet État du serveur cible)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher l'état des serveurs cibles de ce serveur maître.  
  
## <a name="options"></a>Options  
**Serveur cible**  
Affiche le nom du serveur cible.  
  
**Heure locale**  
Affiche la date et l'heure du serveur cible correspondant au fuseau horaire local de ce serveur.  
  
**Dernière interrogation**  
Affiche la date et l'heure locales auxquelles le serveur cible a interrogé pour la dernière fois le serveur maître.  
  
**Instructions non lues**  
Affiche le nombre d'instructions que le serveur cible n'a pas encore reçues.  
  
**État**  
Affiche l'état du serveur cible.  
  
**Forcer l'interrogation**  
Cliquez sur ce bouton pour forcer les serveurs cibles sélectionnés à interroger le serveur maître.  
  
**Forcer la désinscription**  
Cliquez sur ce bouton pour forcer les serveurs cibles sélectionnés à se désinscrire du serveur maître.  
  
**Publier les instructions**  
Publie les instructions sur les serveurs cibles sélectionnés.  
  
**Activer l'actualisation automatique**  
Sélectionnez cette option pour actualiser automatiquement les informations affichées.  
  
**Actualiser toutes les**  
Spécifiez la fréquence à laquelle les informations de cette page doivent être actualisées.  
  
## <a name="see-also"></a> Voir aussi  
[Administration automatisée à l'échelle d'une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)  
