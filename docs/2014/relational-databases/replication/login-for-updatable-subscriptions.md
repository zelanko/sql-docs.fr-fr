---
title: Connexion des abonnements pouvant être mis à jour | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d8162c7654d99cd2ebab41d290c0a39c6c686686
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63058095"
---
# <a name="login-for-updatable-subscriptions"></a>Nom de connexion pour les abonnements pouvant être mis à jour
  Si vous avez sélectionné **répliquer** dans la page **abonnements pouvant être mis à jour** de cet Assistant, vous devez spécifier un compte sur l’abonné sous lequel les connexions au serveur de publication sont effectuées pour les abonnements avec mise à jour immédiate. Les connexions sont utilisées par les déclencheurs qui s'exécutent pour l'abonné et propagent les modifications sur le serveur de publication. Ce compte est requis même si vous avez sélectionné **modifier la file d’attente et valider dès que possible** dans la page **abonnements pouvant être mis** à jour, car par défaut, l’Assistant nouvel abonnement configure la mise à jour en attente avec la possibilité de basculer vers la mise à jour immédiate, si nécessaire.  
  
> [!IMPORTANT]  
>  Le compte spécifié pour la connexion doit uniquement avoir l'autorisation d'insérer, de mettre à jour et de supprimer des données sur les vues créées par la réplication dans la base de données de publication. Il ne doit pas bénéficier d'autres autorisations. Accordez des autorisations sur les vues de la base de données de publication portant le nom sous la forme **syncobj_**_\<HexadecimalNumber>_ au compte que vous avez configuré sur chaque abonné.  
  
 Trois options sont possibles pour le type de connexion :  
  
-   Un serveur lié ou distant que vous avez déjà défini.  
  
-   Un serveur lié créé par la réplication. La connexion se fait à l'aide des informations d'identification spécifiées dans cet Assistant.  
  
-   Un serveur lié créé par la réplication. La connexion se fait à l'aide des informations d'identification de l'utilisateur qui apporte la modification pour l'abonné.  
  
 Vous pouvez spécifier les deux premières options dans cet Assistant. La dernière option peut uniquement être spécifiée à l’aide de [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql); Spécifiez la valeur **1** pour le paramètre **@security_mode**.  
  
## <a name="options"></a>Options  
 **Créez un serveur lié qui se connecte à l’aide de la connexion d’authentification SQL Server suivante :**  
 La réplication crée un serveur lié au moyen des informations d'identification spécifiées dans les champs **Connexion** et **Mot de passe** .  
  
 **Connexion**  
 Entrez une [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion qui dispose uniquement des autorisations décrites dans cette rubrique.  
  
 **Mot de passe**  
 Entrez un mot de passe fort pour la **Connexion**.  
  
 **Confirmer le mot de passe**  
 Entrez une nouvelle fois le mot de passe afin de confirmer qu'il a été saisi correctement.  
  
 **Utiliser un serveur lié ou un serveur distant que vous avez déjà défini.**  
 Cette option nécessite un serveur lié ou distant déjà défini. Pour plus d’informations, consultez [Serveurs liés &#40;moteur de base de données&#41;](../linked-servers/linked-servers-database-engine.md) et [Serveurs distants](../../database-engine/configure-windows/remote-servers.md). Assurez-vous que la connexion utilisée pour le serveur lié ou distant est associée un mot de passe fort et possède uniquement les autorisations décrites dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Afficher et modifier les paramètres de sécurité de la réplication](security/view-and-modify-replication-security-settings.md)   
 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  
