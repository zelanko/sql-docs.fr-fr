---
description: Propriétés de l’alerte - Nouvelle alerte (page Réponse)
title: Propriétés de l’alerte - Nouvelle alerte (page Réponse)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: a29d5064bd480b986ce686dd1202c339a44bfe71
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472520"
---
# <a name="alert-properties---new-alert-response-page"></a>Propriétés de l’alerte - Nouvelle alerte (page Réponse)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour spécifier un travail que vous souhaitez exécuter et pour obtenir une liste d’opérateurs à notifier en réponse à une alerte de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="options"></a>Options  
**Exécuter le travail**  
Active les options **Liste des travaux**, **Nouveau travail** et **Afficher le travail** .  
  
**Nouveau travail**  
Ouvre la boîte de dialogue **Nouveau travail** . Ce bouton n'est pas disponible lorsque **Exécuter le travail** n'est pas sélectionné.  
  
**Afficher le travail**  
Permet d'afficher et de modifier le travail sélectionné. Cette option n'est pas disponible lorsque **Exécuter le travail** n'est pas sélectionné.  
  
**Notifier les opérateurs**  
Active les contrôles qui vous permettent d'ajouter, de supprimer ou de modifier des opérateurs.  
  
**Liste d'opérateurs**  
Répertorie les opérateurs à notifier lorsqu'une alerte se produit. Pour spécifier une méthode de notification, cochez la case **Messagerie électronique**, **Radiomessagerie** ou **Envoi réseau** affichée après le nom de l’opérateur. Cette option n’est pas disponible quand **Notifier les opérateurs** n’est pas sélectionné.  
  
**Messagerie électronique**  
Utilisez un courrier électronique pour notifier l'opérateur.  
  
**Radiomessagerie**  
Utilisez une adresse de radiomessagerie pour notifier l'opérateur.  
  
**Envoi réseau**  
Utilisez **net send** pour notifier l’opérateur.  
  
**Nouvel opérateur**  
Affiche la boîte de dialogue **Nouvel opérateur** , que vous pouvez utiliser pour créer un opérateur.  
  
**Afficher l'opérateur**  
Affiche la boîte de dialogue **Propriétés** pour l’opérateur sélectionné. Vous pouvez afficher et modifier les propriétés d’opérateur dans la boîte de dialogue **Propriétés Opérateur**.  
  
## <a name="see-also"></a>Voir aussi  
[Alertes](../../ssms/agent/alerts.md)  
[Créer une alerte à l'aide d'un niveau de gravité](../../ssms/agent/create-an-alert-using-severity-level.md)  
[Alertes](../../ssms/agent/alerts.md)  
[Modifier une alerte](../../ssms/agent/edit-an-alert.md)  
[Delete an Alert](../../ssms/agent/delete-an-alert.md)  
