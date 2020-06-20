---
title: Sécurité de l’Agent de distribution (réplication d’égal à égal) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.DA.f1
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b95cb43b9321a33be520ee480e3baf203aa4432
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010821"
---
# <a name="distribution-agent-security-peer-to-peer-replication"></a>Sécurité de l'Agent de distribution (réplication d'égal à égal)
  La page **Sécurité de l'Agent de distribution** permet de spécifier les comptes sous lesquels l'Agent de distribution s'exécute et établit les connexions avec les ordinateurs dans une topologie d'égal à égal. Pour plus d’informations sur les autorisations exigées par les agents et les bonnes pratiques en matière de sécurité de la réplication, consultez [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md) et [Bonnes pratiques en matière de sécurité de la réplication](security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Si l'Agent de distribution d'un abonnement a déjà été configuré lors d'une précédente exécution de cet Assistant, vous ne pouvez pas modifier les informations d'identification qu'il utilise dans cet Assistant. Si vous spécifiez de nouvelles informations d'identification, elles sont ignorées. Pour modifier ces informations, utilisez la boîte de dialogue **Propriétés de l'abonnement** . Pour plus d’informations, consultez [afficher et modifier les paramètres de sécurité de la réplication](security/view-and-modify-replication-security-settings.md).  
  
## <a name="options"></a>Options  
 Cliquez sur le bouton de propriétés (**...**) dans la ligne de chaque Abonné pour accéder à la boîte de dialogue **Sécurité de l'Agent de distribution** . Cliquez sur **Aide** dans la boîte de dialogue **Sécurité de l'Agent de distribution** qui s'affiche pour obtenir plus d'informations sur les autorisations indispensables pour les comptes utilisés par les agents.  
  
 Après avoir entré les paramètres dans l'une des boîtes de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agent de l'Abonné**  
 Nom de chaque homologue.  
  
 **Base de données d'homologues**  
 Base de données de l'homologue utilisée à la fois comme base de données de publication et d'abonnement.  
  
 **Connexion au serveur de distribution**  
 Le contexte dans lequel la connexion au serveur de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent. Cet Assistant crée des abonnements par émission (la connexion locale est la connexion au serveur de distribution), de sorte que ce champ affiche toujours : **emprunter l’identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '**.  
  
 **Connexion à l'Abonné**  
 Le contexte dans lequel la connexion à l'abonné s'établit. Il est possible d'établir la connexion en utilisant le contexte du compte Windows sous lequel s'exécute l'agent ou le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ affiche l’un des éléments suivants : **utiliser la connexion' \<Login> '**, emprunter l' **identité' \<Domain> \\<connexion \> '** ou **emprunter l’identité' \<Computer> \\<connexion \> '**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer une topologie d’égal à égal &#40;la programmation Transact-SQL de la réplication&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Réplication transactionnelle d’égal à égal](transactional/peer-to-peer-transactional-replication.md)  
  
  
