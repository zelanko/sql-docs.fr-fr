---
description: Nom de connexion pour les abonnements pouvant être mis à jour
title: Connexion des abonnements pouvant être mis à jour | Microsoft Docs
ms.custom: ''
ms.date: 08/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81a455310e419eaac0136721d021e700fa29f136
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493924"
---
# <a name="login-for-updatable-subscriptions"></a>Nom de connexion pour les abonnements pouvant être mis à jour
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Pour une mise à jour immédiate, si vous avez sélectionné **Répliquer** dans la page **Abonnements pouvant être mis à jour** de cet Assistant, vous devez spécifier un compte avec l’Abonné sous lequel les connexions au serveur de publication s’effectuent. 
  
 Les connexions sont utilisées par les déclencheurs qui sont activés pour l’Abonné et propagent les modifications sur le serveur de publication. Ce compte est nécessaire même si vous avez sélectionné **Mettre les modifications en file d’attente et valider dès que possible** dans la page **Abonnements pouvant être mis à jour**. L’Assistant Nouvel abonnement par défaut configure la mise à jour en attente avec la possibilité de passer à une mise à jour immédiate si nécessaire.  
  
> **IMPORTANT** Le compte spécifié pour la connexion doit uniquement avoir l’autorisation d’insérer, de mettre à jour et de supprimer des données sur les vues créées par la réplication dans la base de données de publication. Il ne doit pas bénéficier d’autres autorisations. Octroyez des autorisations sur les vues de la base de données de publication qui sont mentionnées dans le panneau **syncobj_** _\<HexadecimalNumber>_ pour le compte que vous avez configuré pour chaque abonné.  
  
 Trois options sont possibles pour le type de connexion :  
  
-   Un serveur lié ou distant que vous avez déjà défini.  
  
-   Un serveur lié créé par la réplication. La connexion se fait à l'aide des informations d'identification spécifiées dans cet Assistant.  
  
-   Un serveur lié créé par la réplication. La connexion se fait à l'aide des informations d'identification de l'utilisateur qui apporte la modification pour l'abonné.  
  
 Vous pouvez spécifier les deux premières options dans cet Assistant. La dernière option peut uniquement être spécifiée à l’aide de [sp_link_publication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Spécifiez la valeur **1** pour le paramètre `@security_mode`.  
  
## <a name="options"></a>Options  
 **Créer un serveur lié qui se connecte par une connexion d'authentification SQL Server :**  
 La réplication crée un serveur lié au moyen des informations d'identification spécifiées dans les champs **Connexion** et **Mot de passe** .  
  
 **Connexion**  
 Entrez un nom de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui bénéficie uniquement des autorisations décrites dans cette rubrique.  
  
 **Mot de passe**  
 Entrez un mot de passe fort pour la **Connexion**.  
    
 **Utiliser un serveur lié ou un serveur distant que vous avez déjà défini.**  
 Cette option nécessite un serveur lié ou distant déjà défini. Pour plus d’informations, consultez [Serveurs liés &#40;moteur de base de données&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) et [Serveurs distants](../../database-engine/configure-windows/remote-servers.md). Assurez-vous que la connexion utilisée pour le serveur lié ou distant est associée un mot de passe fort et possède uniquement les autorisations décrites dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
