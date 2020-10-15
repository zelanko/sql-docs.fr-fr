---
description: Créer un événement défini par l'utilisateur
title: Créer un événement défini par l'utilisateur
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bf18385b89ac7af32bfde26d704880eb4e9bb300
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036654"
---
# <a name="create-a-user-defined-event"></a>Créer un événement défini par l'utilisateur
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Vous pouvez créer des événements définis par l'utilisateur si vous voulez surveiller d'autres événements que ceux qui sont prédéfinis par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez également attribuer un niveau de sévérité à chaque événement défini par l'utilisateur.  
  
> [!NOTE]  
> Quand vous utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionnez l’option **Enregistrer dans le journal des événements** pour chaque message d’événement défini par l’utilisateur, pour vous assurer que les messages seront journalisés. Par défaut, les messages définis par l'utilisateur de sévérité inférieure à 19 ne sont pas envoyés au journal des applications [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows lorsqu'ils se produisent. Par conséquent, les messages définis par l'utilisateur de sévérité inférieure à 19 ne déclenchent pas d'alertes au niveau de l'Agent SQL Server.  
  
Les événements définis par l'utilisateur doivent posséder un numéro de message unique. Les numéros de message liés à un événement défini par l'utilisateur doivent être supérieurs à 50 000. Vous pouvez définir des messages pour l'événement dans plusieurs langues. Cependant, un message **En-US** doit exister avant que des messages correspondant à d’autres langues puissent être ajoutés.  
  
Si vous administrez un environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] multilingue, créez des messages définis par l'utilisateur dans chacune des langues prises en charge par le système. Par exemple, si vous créez un nouveau message d'événement qui sera utilisé aussi bien sur un serveur anglais que sur un serveur allemand, vous devez utiliser le même numéro d'événement et le même niveau de sévérité pour les deux, mais leur affecter un message dans une langue différente.  
  
Les tâches suivantes apportent des informations sur la façon de créer des événements définis par l'utilisateur, ainsi que des alertes qui leur répondent :  
  
**Pour créer une alerte en fonction d'un numéro de message**  
  
-   [SQL Server Management Studio](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)  
  
**Pour créer une alerte en fonction de niveaux de gravité**  
  
-   [SQL Server Management Studio](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)  
  
**Pour définir la réponse à une alerte**  
  
-   [SQL Server Management Studio](../../ssms/agent/define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)  
  
**Pour créer un message d'erreur d'événement défini par l'utilisateur**  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)  
  
**Pour modifier un message d'erreur d'événement défini par l'utilisateur**  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)  
  
**Pour supprimer un message d'erreur d'événement défini par l'utilisateur**  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)  
  
**Pour désactiver ou réactiver une alerte**  
  
-   [SQL Server Management Studio](../../ssms/agent/disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
[sp_update_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)  
