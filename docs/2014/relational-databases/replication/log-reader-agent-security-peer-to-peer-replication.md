---
title: Sécurité de l’Agent de lecture du journal (réplication d’égal à égal) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d6bcf7d78fd550404f81f9cc303414303ad82504
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63000356"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a>Sécurité de l'Agent de lecture du journal (réplication d'égal à égal)
  La page sécurité de l' **agent de lecture du journal** vous permet de spécifier les comptes sous lesquels l’agent de lecture du journal sur chaque homologue s’exécute et établit des connexions. Pour plus d’informations sur les autorisations exigées par les agents et les bonnes pratiques méthodes pour la sécurité de la réplication, consultez [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md) et [Bonnes pratiques en matière de sécurité de réplication](security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Il existe un Agent de lecture du journal pour chaque base de données publiée utilisant la réplication transactionnelle. Si l'Agent de lecture du journal d'une base de données est déjà configuré (pour la publication dans une exécution précédente de cet Assistant ou une autre publication transactionnelle dans la même base de données), vous ne pouvez pas modifier les informations d'identification qu'il utilise dans l'Assistant. Si vous spécifiez de nouvelles informations d'identification, elles sont ignorées. Pour changer les informations d'identification, utilisez la boîte de dialogue **Propriétés de la publication** . Pour plus d’informations, consultez [afficher et modifier les paramètres de sécurité de la réplication](security/view-and-modify-replication-security-settings.md).  
  
## <a name="options"></a>Options  
 Cliquez sur le bouton avec des points de suspension (**...**) dans la ligne de chaque homologue pour accéder à la boîte de dialogue **Sécurité de l'Agent de lecture du journal** . Cliquez sur **Aide** dans la boîte de dialogue **Sécurité de l'Agent de lecture du journal** qui s'ouvre pour plus d'informations sur les autorisations nécessaires aux comptes utilisés par les agents.  
  
 Après avoir défini les paramètres de la boîte de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agents du serveur de publication**  
 Nom de chaque instance de serveur homologue.  
  
 **Base de données d’homologue**  
 Base de données qui fait office de base de données de publication et de base de données d'abonnement sur chaque homologue.  
  
 **Connexion au serveur de distribution**  
 Le contexte dans lequel la connexion au serveur de distribution s'établit. La connexion locale au serveur de distribution est toujours établie en utilisant le contexte du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l’Agent s’exécute. Par conséquent, ce champ contient toujours **Emprunter l’identité '\<Domaine>\\<Connexion>\>'** ou **Emprunter l’identité '\<Ordinateur>\\<Connexion>\>'**.  
  
 **Connexion au serveur de publication**  
 Contexte sous lequel la connexion au serveur de publication est établie. La connexion au serveur de publication peut être établie à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’aide d’une connexion ou à l’aide du contexte du compte Windows sous lequel l’agent s’exécute. Le champ contient l’un des éléments suivants : **Utiliser la connexion \<Connexion>**, **Emprunter l’identité \<Domaine>\\<Connexion\>** ou **Emprunter l’identité\<Ordinateur>\\<Connexion\>**. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer une topologie d’égal à égal &#40;programmation Transact-SQL de la réplication&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)  
  
  
