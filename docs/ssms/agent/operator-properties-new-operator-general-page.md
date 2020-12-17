---
description: Propriétés de l’opérateur - Nouvel opérateur (page Général)
title: Propriétés de nouvel opérateur (page Général)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: de726644bbd239dfe095a1c2a1860d95f213eb29
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97408851"
---
# <a name="operator-properties---new-operator-general-page"></a>Propriétés de l’opérateur - Nouvel opérateur (page Général)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et modifier les propriétés générales des opérateurs de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Nom**  
Permet de modifier le nom de l'opérateur.  
  
**Enabled**  
Permet d'activer l'opérateur. Aucune notification n'est envoyée à l'opérateur lorsque cette option est désactivée.  
  
**Nom de messagerie électronique**  
Spécifie l'adresse de messagerie de l'opérateur.  
  
**Adresse d'envoi réseau**  
Spécifie l’adresse à utiliser pour **net send**.  
  
**Nom de l'adresse de radiomessagerie**  
Spécifie l'adresse de messagerie à utiliser pour la radiomessagerie de l'opérateur.  
  
**Planification de la radiomessagerie active**  
Définit les périodes d'activité de la radiomessagerie.  
  
**Lundi - Dimanche**  
Permet de sélectionner les jours d'activité de la radiomessagerie.  
  
**Début de journée**  
Sélectionne l’heure après laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent envoie des messages à la radiomessagerie.  
  
**Fin de journée**  
Sélectionne l’heure après laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n’envoie plus de messages à la radiomessagerie.  
  
## <a name="see-also"></a>Voir aussi  
[Opérateurs](../../ssms/agent/operators.md)  
