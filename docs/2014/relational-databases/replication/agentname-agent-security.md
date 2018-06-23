---
title: Sécurité de l’agent &lt;nom_agent&gt; | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e0d562e0fee10e4533153dfe4fcf4e4be780dcd2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043120"
---
# <a name="ltagentnamegt-agent-security"></a>Sécurité de l’agent &lt;nom_agent&gt;
  La page **\<Sécurité de l’agent <nom_agent>** permet de spécifier les comptes sous lesquels l’Agent de distribution (pour la réplication transactionnelle ou la réplication de capture instantanée) ou l’Agent de fusion (pour la réplication de fusion) s’exécutent et établissent les connexions aux ordinateurs d’une topologie de réplication. Pour plus d’informations sur les autorisations exigées par les agents et les bonnes pratiques en matière de sécurité de la réplication, consultez [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md) et [Bonnes pratiques en matière de sécurité de la réplication](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Options  
 Cliquez sur le bouton de propriétés (**...**) dans la ligne de chaque Abonné pour accéder à la boîte de dialogue **Sécurité de l'Agent de distribution** ou **Sécurité de l'Agent de fusion** . Cliquez sur **Aide** dans la boîte de dialogue qui s'affiche pour fournir plus d'informations sur les autorisations indispensables pour les comptes utilisés par les agents.  
  
 Après avoir entré les paramètres dans l'une des boîtes de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agent de l'Abonné**  
 Nom de chaque Abonné.  
  
 **Connexion au serveur de distribution**  
 S'affiche pour les réplications d'instantané et transactionnelle. Le contexte dans lequel la connexion au serveur de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par émission de données, la connexion locale est celle qui est établie au serveur de distribution, de sorte que ce champ affiche toujours : **Emprunter l’identité \<Domain>\\<Login\>** ou **Emprunter l’identité \<Computer>\\<Login\>** pour les abonnements par émission de données.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ contient l’un des éléments suivants : **Utiliser la connexion \<Connexion>****, Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité\<Ordinateur>\\<Connexion\>**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion au serveur de publication et serveur de distribution**  
 S'affiche pour la réplication de fusion. Le contexte des connexions aux serveurs de publication et de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par émission de données, la connexion locale est celle qui est établie au serveur de publication et au serveur de distribution, de sorte que ce champ affiche toujours : **Emprunter l’identité \<Domain>\\<Login\>** ou **Emprunter l’identité \<Computer>\\<Login\>** pour les abonnements par émission de données.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ contient l’un des éléments suivants : **Utiliser la connexion \<Connexion>****, Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité\<Ordinateur>\\<Connexion\>**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion à l'Abonné**  
 Le contexte dans lequel la connexion à l'abonné s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par extraction, la connexion locale est celle qui est établie à l’Abonné, de sorte que ce champ affiche toujours : **Emprunter l’identité \<Domain>\\<Login\>** ou **Emprunter l’identité \<Computer>\\<Login\>** pour les abonnements par émission de données.  
  
-   Pour les abonnements par émission de données, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ contient l’un des éléments suivants : **Utiliser la connexion \<Connexion>****, Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité\<Ordinateur>\\<Connexion\>**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md)   
 [Afficher et modifier les propriétés d’un abonnement par émission de données](view-and-modify-push-subscription-properties.md)   
 [Gérer les comptes de connexion et les mots de passe dans la réplication](security/manage-logins-and-passwords-in-replication.md)   
 [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md)   
 [Sécurité et protection &#40;Réplication&#41;](security/security-and-protection-replication.md)  
  
  