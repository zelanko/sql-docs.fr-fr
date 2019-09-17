---
title: Envoyer un e-mail de test avec Database Mail | Microsoft Docs
ms.custom: ''
ms.date: 04/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8412a87703577595f0408de3b9cf26520160fdf
ms.sourcegitcommit: 2da98f924ef34516f6ebf382aeb93dab9fee26c1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70228456"
---
# <a name="send-a-test-email-with-database-mail"></a>Envoyer un e-mail de test avec Database Mail  
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Utilisez la boîte de dialogue Envoyer un message électronique de test pour tester la capacité d’un profil spécifique à envoyer des messages.

## <a name="permissions"></a>Autorisations

Vous devez être membre du rôle serveur fixe sysadmin pour pouvoir utiliser la boîte de dialogue Envoyer un message électronique de test. Les utilisateurs qui ne sont pas membres du rôle serveur fixe sysadmin peuvent tester Database Mail à l’aide de la procédure [sp_send_dbmail](../system-stored-procedures/sp-send-dbmail-transact-sql.md).

## <a name="procedure"></a>Procédure

1. À l’aide de l’Explorateur d’objets dans [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md), connectez-vous à une instance du moteur de base de données SQL Server où Database Mail est configuré, développez Gestion, cliquez avec le bouton droit sur Database Mail, puis sélectionnez Envoyer un message électronique de test. S’il n’existe aucun profil Database Mail, une boîte de dialogue invite l’utilisateur à en créer un et ouvre l’Assistant Configuration de Database Mail.
1. Dans la boîte de dialogue **Envoyer un message électronique de test à partir de** <instance name>, dans la zone Profil Database Mail, sélectionnez le profil à tester.
1. Dans la zone **À**, tapez l’adresse e-mail du destinataire de l’e-mail de test.
1. Dans la zone **Objet**, tapez l’objet de l’e-mail de test. Modifiez le texte d’objet par défaut pour mieux identifier le message à des fins de dépannage.
1. Dans la zone **Corps**, tapez le texte de l’e-mail de test. Modifiez le texte d’objet par défaut pour mieux identifier le message à des fins de dépannage.
1. Sélectionnez **Envoyer un message électronique de test** pour envoyer l’e-mail de test dans la file d’attente de Database Mail.
1. L’envoi de l’e-mail de test ouvre la boîte de dialogue E-mail de test de Database Mail. Notez le chiffre affiché dans la zone Message envoyé. Il s’agit de la valeur mailitem_id de l’e-mail de test. Sélectionnez OK.
1. Dans la barre d’outils, sélectionnez Nouvelle requête pour ouvrir une fenêtre de l’Éditeur de requête. Exécutez l’instruction T-SQL suivante pour déterminer l’état de l’e-mail de test :

    ```sql
    SELECT * FROM msdb.dbo.sysmail_allitems 
    WHERE mailitem_id = <the mailitem_id from the previous step> ;
    ```

    La colonne sent_status indique si l’e-mail de test a été envoyé.

1. En cas d’erreur, exécutez l’instruction suivante pour afficher le message d’erreur :

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    ```sql
    SELECT * FROM msdb.dbo.sysmail_event_log 
    WHERE mailitem_id = <the mailitem_id from the previous step> ;
    ```


##  <a name="RelatedContent"></a> Voir aussi 
  
-   [Objets de configuration de la messagerie de base de données](../../relational-databases/database-mail/database-mail-configuration-objects.md)
-   [Objets de messagerie de base de données](../../relational-databases/database-mail/database-mail-messaging-objects.md)
-   [Programme externe de la messagerie de base de données](../../relational-databases/database-mail/database-mail-external-program.md)
-   [Journal et audits de la messagerie de base de données](../../relational-databases/database-mail/database-mail-log-and-audits.md)
-   [Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)
  
  
