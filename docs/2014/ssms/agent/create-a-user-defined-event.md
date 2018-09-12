---
title: Créer un événement défini par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b96e6966afd08b03b086ca61f6e827c1c38c96ef
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820075"
---
# <a name="create-a-user-defined-event"></a>Créer un événement défini par l'utilisateur
  Vous pouvez créer des événements définis par l'utilisateur si vous voulez surveiller d'autres événements que ceux qui sont prédéfinis par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez également attribuer un niveau de sévérité à chaque événement défini par l'utilisateur.  
  
> [!NOTE]  
>  Quand vous utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionnez l’option **Enregistrer dans le journal des événements** pour chaque message d’événement défini par l’utilisateur, pour vous assurer que les messages seront journalisés. Par défaut, les messages définis par l'utilisateur de sévérité inférieure à 19 ne sont pas envoyés au journal des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows lorsqu'ils se produisent. Par conséquent, les messages définis par l'utilisateur de sévérité inférieure à 19 ne déclenchent pas d'alertes au niveau de l'Agent SQL Server.  
  
 Les événements définis par l'utilisateur doivent posséder un numéro de message unique. Les numéros de message liés à un événement défini par l'utilisateur doivent être supérieurs à 50 000. Vous pouvez définir des messages pour l'événement dans plusieurs langues. Cependant, un message **En-US** doit exister avant que des messages correspondant à d’autres langues puissent être ajoutés.  
  
 Si vous administrez un environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] multilingue, créez des messages définis par l'utilisateur dans chacune des langues prises en charge par le système. Par exemple, si vous créez un nouveau message d'événement qui sera utilisé aussi bien sur un serveur anglais que sur un serveur allemand, vous devez utiliser le même numéro d'événement et le même niveau de sévérité pour les deux, mais leur affecter un message dans une langue différente.  
  
 Les tâches suivantes apportent des informations sur la façon de créer des événements définis par l'utilisateur, ainsi que des alertes qui leur répondent :  
  
 **Pour créer une alerte en fonction d'un numéro de message**  
  
-   [SQL Server Management Studio](create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **Pour créer une alerte en fonction de niveaux de gravité**  
  
-   [SQL Server Management Studio](create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **Pour définir la réponse à une alerte**  
  
-   [SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 **Pour créer un message d'erreur d'événement défini par l'utilisateur**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 **Pour modifier un message d'erreur d'événement défini par l'utilisateur**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 **Pour supprimer un message d'erreur d'événement défini par l'utilisateur**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 **Pour désactiver ou réactiver une alerte**  
  
-   [SQL Server Management Studio](disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
  
