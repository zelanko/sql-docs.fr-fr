---
title: Créer un compte de messagerie de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], accounts
- accounts [Database Mail]
ms.assetid: c07abbc6-fc6a-470b-8fa3-532f2e06b16a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a286c7d4c0ff42389830713a6c42c89a7273f1d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917726"
---
# <a name="create-a-database-mail-account"></a>Créer un compte de messagerie de base de données
  Utilisez l' **Assistant Configuration de la messagerie de base de données** ou [!INCLUDE[tsql](../../includes/tsql-md.md)] pour créer un compte de messagerie de base de données.  
  
-   **Avant de commencer :**  [Prérequis](#Prerequisites)  
  
-   **Pour créer un base de données compte de messagerie à l’aide :**  [ Assistant Configuration de Database Mail](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Étapes suivantes pour configurer la messagerie de base de données](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Déterminez le nom de serveur et le numéro de port du serveur SMTP (Simple Mail Transfer Protocol) utilisé pour l'envoi du courrier électronique. Si le serveur SMTP nécessite une authentification, déterminez le nom d'utilisateur et le mot de passe du serveur SMTP.  
  
-   Si vous le souhaitez, vous pouvez également spécifier le type de serveur et le numéro de port du serveur. Le type de serveur est toujours SMTP pour le courrier sortant. La plupart des serveurs SMTP utilisent le numéro de port par défaut 25.  
  
##  <a name="SSMSProcedure"></a> Utilisation de l'Assistant Configuration de la messagerie de base de données  
 **Pour créer un compte de messagerie de base de données à l'aide d'un Assistant**  
  
-   Dans l'Explorateur d'objets, connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle vous voulez configurer la messagerie de base de données, puis développez l'arborescence du serveur.  
  
-   Développez le nœud **Gestion** .  
  
-   Double-cliquez sur Messagerie de base de données pour ouvrir l'Assistant Configuration de la messagerie de base de données.  
  
-   Dans la page **Sélectionner une tâche de configuration** , sélectionnez **Gérer les comptes et les profils de messagerie de base de données**, puis cliquez sur **Suivant**.  
  
-   Dans la page **Gérer les profils et les comptes** , sélectionnez **Créer un nouveau compte** , puis cliquez sur **Suivant**.  
  
-   Dans la page **Nouveau compte** , spécifiez le nom du compte, sa description, les informations du serveur de messagerie et le type d'authentification. Cliquez sur **Suivant**.  
  
-   Dans la page **Terminer l'Assistant** , examinez les actions à exécuter, puis cliquez sur **Terminer** pour terminer la création du nouveau compte.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour créer un compte de messagerie de base de données à l'aide de Transact-SQL**  
  
 Exécutez la procédure stockée **msdb.dbo.sysmail_add_account_sp** pour créer le compte et spécifiez les informations suivantes :  
  
-   Le nom du compte à créer.  
  
-   Une description facultative du compte.  
  
-   L'adresse électronique à afficher sur les messages électroniques sortants.  
  
-   Le nom complet à afficher sur les messages électroniques sortants.  
  
-   Le nom du serveur SMTP.  
  
-   Le nom d'utilisateur à utiliser pour la connexion au serveur SMTP, si celui-ci nécessite une authentification.  
  
-   Le mot de passe à utiliser pour la connexion au serveur SMTP, si celui-ci nécessite une authentification.  
  
 L'exemple ci-dessous crée un compte de messagerie de base de données.  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
##  <a name="FollowUp"></a> Suivi : Étapes suivantes pour configurer la messagerie de base de données  
  
-   [Créer un profil de messagerie de base de données](create-a-database-mail-profile.md)  
  
  
