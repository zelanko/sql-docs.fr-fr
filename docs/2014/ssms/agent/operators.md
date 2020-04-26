---
title: Opérateurs | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- operators (users) [Database Engine]
- fail-safe operator [SQL Server]
- aliases [SQL Server], operators
- SQL Server Agent alerts, operators
- contact information [SQL Server Agent]
- net send [SQL Server]
- e-mail [SQL Server], SQL Server Agent operators
- pager notifications [SQL Server Agent]
- mail [SQL Server], SQL Server Agent operators
- operators (users) [Database Engine], defining
- jobs [SQL Server Agent], operators
- alerts [SQL Server], operators
ms.assetid: 38e8488f-2669-4cea-b9c3-5f394a663678
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 03deab738f374716002c4d78e07078e90fb41822
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68189018"
---
# <a name="operators"></a>Opérateurs
  Les opérateurs sont des alias pour les personnes ou les groupes qui peuvent recevoir une notification électronique à la fin des travaux ou en cas d'alertes. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prend en charge la notification des administrateurs par le biais des opérateurs. Les opérateurs activent les fonctions de notification et de surveillance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="operator-attributes-and-concepts"></a>Attributs et concepts relatifs aux opérateurs  
 Les attributs principaux d'un opérateur sont les suivants :  
  
-   Nom de l'opérateur  
  
-   Informations de contact  
  
### <a name="naming-an-operator"></a>Désignation d'un opérateur  
 Chaque opérateur doit avoir un nom. Les noms des opérateurs doivent être uniques dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ne pas dépasser **128** caractères.  
  
### <a name="contact-information"></a>Informations de contact  
 Les informations de contact d'un opérateur définissent la façon dont l'opérateur est notifié. Les opérateurs peuvent être avertis par e-mail, par radiomessagerie ou par la commande **net send** :  
  
> [!IMPORTANT]  
>  Les options de radiomessagerie et **net send** seront [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprimées de l’agent dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]une version ultérieure de. Évitez d'utiliser ces fonctionnalités dans une nouvelle tâche de développement et prévoyez de modifier les applications qui les utilisent actuellement.  
  
-   **Notification par e-mail**  
  
     La notification par courrier électronique envoie un message électronique à l'opérateur. Fournissez l'adresse électronique de l'opérateur.  
  
-   **Notification par radiomessagerie**  
  
     La radiomessagerie est mise en place à l'aide du courrier électronique. Fournissez l'adresse électronique de l'opérateur à laquelle il recevra les messages de radiomessagerie. Pour définir une notification par radiomessagerie, vous devez installer sur le serveur de messagerie un logiciel qui traite le courrier entrant et qui le convertit en message de radiomessagerie. Plusieurs approches sont possibles avec le logiciel, notamment :  
  
    -   transmettre le courrier à un serveur de messagerie distant sur le site du fournisseur de radiomessagerie ;  
  
         Le fournisseur de services de radiomessagerie doit offrir ce service, même si le logiciel nécessaire fait généralement partie du système de messagerie électronique local. Pour plus d'informations, consultez la documentation relative à votre récepteur de radiomessagerie.  
  
    -   acheminer le courrier sur le réseau Internet vers un serveur de messagerie sur le site du fournisseur de services de radiomessagerie ;  
  
         Il s'agit d'une variation de la première approche.  
  
    -   traiter le courrier entrant et composer le numéro du récepteur de radiomessagerie à l'aide d'un modem auxiliaire.  
  
         Ce logiciel est propre au fournisseur de services de radiomessagerie. Le logiciel fait office de client de courrier électronique qui traite régulièrement sa boîte de réception en interprétant tout ou partie des informations relatives aux adresses de courrier électronique comme un numéro de récepteur de radiomessagerie, ou en comparant le nom associé au courrier électronique à un numéro de récepteur de radiomessagerie dans une table de correspondance.  
  
         Si tous les opérateurs ont le même fournisseur de services de radiomessagerie, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour spécifier une mise en forme spécifique de courrier électronique exigé par le système de liaison par radiomessagerie/courrier électronique. Cette mise en forme spéciale peut être un préfixe ou un suffixe et elle peut être incluse dans les lignes suivantes du courrier électronique :  
  
         **Objet:**  
  
         **Cc** :  
  
         **À** :  
  
    > [!NOTE]  
    >  Si vous utilisez un système de radiomessagerie alphanumérique à faible capacité, vous pouvez raccourcir le texte à envoyer en éliminant le texte d'erreur de la notification par radiomessagerie. C'est le cas par exemple des systèmes limités à 64 caractères par page.  
  
-   **Notification net send**  
  
     Envoie un message à l’opérateur par le biais de la commande **net send** . Pour **net send**, spécifiez le destinataire (ordinateur ou utilisateur) du message réseau.  
  
    > [!NOTE]  
    >  La commande **net send** utilise Microsoft Windows Messenger. Pour envoyer des alertes, ce service doit s'exécuter à la fois sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute et sur l'ordinateur de l'opérateur.  
  
## <a name="alerting-and-fail-safe-operators"></a>Alertes et opérateurs de prévention de défaillance  
 Vous pouvez choisir les opérateurs à avertir en réponse à une alerte. Par exemple, vous pouvez attribuer des responsabilités alternées aux opérateurs, en planifiant des alertes qui les avertissent. Ainsi, une personne A peut être avertie des alertes intervenant le lundi, le mercredi ou le vendredi, tandis qu'une personne B peut l'être le mardi, le jeudi ou le samedi.  
  
 L'opérateur de prévention de défaillance reçoit une notification d'alerte après l'échec de toutes les notifications par radiomessagerie envoyées aux opérateurs désignés. Si, par exemple, vous définissez trois opérateurs à avertir par radiomessagerie et qu'aucun des trois ne peut être contacté, l'opérateur de prévention de défaillance est averti.  
  
 L'opérateur de prévention de défaillance est averti lorsque :  
  
-   les opérateurs responsables de l'alerte n'ont pas pu être contactés par radiomessagerie ;  
  
     Cela peut être dû à l'impossibilité de joindre les principaux opérateurs, par exemple si les adresses de radiomessagerie sont incorrectes ou si les opérateurs ne sont pas en service.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne peut pas avoir accès aux tables système de la base de données **msdb** .  
  
     La table système **sysnotifications** précise les responsabilités des opérateurs en ce qui concerne les alertes.  
  
 L'opérateur de prévention de défaillance est une fonction de sécurité. Vous ne pouvez pas supprimer l'opérateur affecté en tant que tel sans réaffecter la prévention de défaillance à un autre opérateur ou sans supprimer aussi cette sécurité.  
  
## <a name="notifying-an-operator"></a>Envoi d'une notification à un opérateur  
 Un ou plusieurs des éléments suivants sont nécessaires pour avertir un opérateur :  
  
-   Pour envoyer un courrier électronique à l'aide de la fonction de messagerie de base de données, vous devez avoir accès à un serveur de messagerie prenant en charge le protocole SMTP.  
  
-   Pour la transmission par radiomessagerie, vous devez disposer d'un logiciel et/ou matériel de transmission de radiomessagerie à courrier électronique.  
  
-   Pour utiliser **net send**, l’opérateur doit avoir ouvert une session sur l’ordinateur spécifié et ce dernier doit accepter les messages en provenance de Windows Messenger.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Tâches**|**Rubrique**|  
|Tâches associées à la création d'un opérateur|[Créer un opérateur](create-an-operator.md)<br /><br /> [Désigner un opérateur de prévention de défaillance](designate-a-fail-safe-operator.md)|  
|Tâches associées à l'affectation d'alertes|[Assign Alerts to an Operator](assign-alerts-to-an-operator.md)<br /><br /> [Définir la réponse à une alerte &#40;SQL Server Management Studio&#41;](define-the-response-to-an-alert-sql-server-management-studio.md)<br /><br /> [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)<br /><br /> [Assign Alerts to an Operator](assign-alerts-to-an-operator.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
