---
title: Bonnes pratiques en matière de sécurité de la réplication | Microsoft Docs
description: Découvrez la meilleure approche pour sécuriser les connexions de réplication dans SQL Server dans différentes circonstances.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server replication], best practices
- security [SQL Server replication], between domains
- authentication [SQL Server replication]
- Internet [SQL Server replication], security
ms.assetid: 1ab2635d-0992-4c99-b17d-041d02ec9a7c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f2b45cde8e2ab16e97e17a72a51cd147203c2e51
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893778"
---
# <a name="replication-security-best-practices"></a>Méthodes préconisées en matière de sécurité de réplication
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  La réplication permet de déplacer des données d'environnements distribués qui englobent tant des intranets sur un domaine unique que des applications accédant à des données entre des domaines non approuvés et sur Internet. Il est important de bien connaître toutes les méthodes de sécurisation des connexions de réplication afin de choisir celle qui répond le mieux à la situation.  
  
 Les informations suivantes concernent la réplication dans tous les environnements :  
  
-   Chiffrez les connexions entre des ordinateurs d'une topologie de réplication à l'aide d'une méthode standard dans l'industrie, telle que les réseaux privés virtuels (VPN, Virtual Private Networks), TLS (Transport Layer Security), précédemment appelé SSL (Secure Sockets Layer), et IPSEC (IP Security). Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md). Pour plus d'informations sur l'utilisation des réseaux VPN et de TLS pour répliquer les données sur Internet, consultez [Securing Replication Over the Internet](../../../relational-databases/replication/security/securing-replication-over-the-internet.md).  
  
     Si vous utilisez TLS pour sécuriser les connexions entre ordinateurs dans une topologie de réplication, spécifiez la valeur **1** ou **2** pour le paramètre **-EncryptionLevel** de chaque agent de réplication (la valeur **2** est recommandée). La valeur **1** spécifie que le chiffrement est utilisé, mais que l'agent ne vérifie pas si le certificat de serveur TLS/SSL est signé par un émetteur fiable ; la valeur **2** indique que le certificat est vérifié. Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez les pages suivantes :  
  
    -   [Utiliser des profils d’agent de réplication](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Afficher et modifier des paramètres d’invite de commandes d’un Agent de réplication &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Concepts des exécutables de l'agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
-   Exécutez chaque agent de réplication sous un compte Windows différent et utilisez l'authentification Windows pour toutes les connexions des agents de réplication. Pour plus d’informations sur la spécification de comptes, consultez [Identité et contrôle d’accès pour la réplication](../../../relational-databases/replication/security/identity-and-access-control-replication.md).  
  
-   Accordez à chaque agent les autorisations dont ils ont besoin et pas davantage. Pour plus d'informations, consultez la section « Autorisations requises par les agents » de [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
-   Vérifiez que tous les comptes de l'Agent de fusion et de l'Agent de distribution figurent dans la liste d'accès à la publication. Pour plus d’informations, consultez [Sécuriser le serveur de publication](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
-   Suivez le principe du moindre privilège en n'accordant aux comptes de la liste d'accès à la publication que les autorisations nécessaires pour effectuer des tâches de réplication. N'ajoutez pas de connexions inutiles pour la réplication aux rôles de serveur fixe.  
  
-   Configurez le partage d'instantanés de telle sorte que tous les Agent de fusion et tous les Agents de distribution puissent disposer d'un accès en lecture. Dans le cas d'instantanés pour des publications avec des filtres paramétrés, vérifiez que chaque dossier est configuré pour n'autoriser l'accès qu'aux comptes appropriés de l'Agent de fusion.  
  
-   Configurez le partage d'instantanés de telle sorte que l'Agent d'instantané puisse disposer d'un accès en écriture.  
  
-   Si vous utilisez des abonnements par extraction de données (pull), préférez l'utilisation d'un partage réseau à un chemin d'accès local du dossier d'instantanés.  
  
 Si votre topologie de réplication comprend des ordinateurs qui se trouvent dans des domaines différents ou dans des domaines sans relations de confiance, vous pouvez utiliser l'authentification Windows ou l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour les connexions établies par des agents (pour plus d'informations sur les domaines, consultez la cocumentation Windows). L'authentification Windows est une méthode de sécurité préconisée.  
  
-   Pour utiliser l'authentification Windows  
  
    -   Ajoutez un compte Windows local (et non un compte de domaine) pour chaque agent sur les nœuds appropriés (utilisez le même nom et le même mot de passe sur chaque nœud). Par exemple, l'Agent de distribution d'un abonnement par envoi de données (push) s'exécute sur le serveur de distribution et établit des connexions avec le serveur de distribution et l'Abonné. Le compte Windows de l'Agent de distribution doit être ajouté au serveur de distribution et à l'Abonné.  
  
    -   Vérifiez qu'un agent donné (par exemple, l'Agent de distribution pour un abonnement) s'exécute sous le même compte sur chaque ordinateur.  
  
-   Pour utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
    -   Ajoutez un compe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour chaque agent sur les nœuds appropriés (utilisez le même nom de compte et le même mot de passe sur chaque nœud). Par exemple, l'Agent de distribution d'un abonnement par envoi de données (push) s'exécute sur le serveur de distribution et établit des connexions avec le serveur de distribution et l'Abonné. Le compte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de l'Agent de distribution doit être ajouté au serveur de distribution et à l'Abonné.  
  
    -   Vérifiez qu'un agent donné (par exemple, l'Agent de distribution d'un abonnement) établit des connexions sous le même compte sur chaque ordinateur.  
  
    -   Dans les situations exigeant l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , l'accès aux partages d'instantanés UNC n'est souvent pas disponible (par exemple, l'accès peut être bloqué par un pare-feu). Dans ce cas, vous pouvez transférer l'instantané aux abonnés via FTP (File Transfer Protocol). Pour plus d’informations, consultez [Transférer des instantanés via FTP](../../../relational-databases/replication//publish/deliver-a-snapshot-through-ftp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Activer les connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)   
 [Réplication sur Internet](../../../relational-databases/replication/replication-over-the-internet.md)   
 [Sécuriser l’abonné](../../../relational-databases/replication/security/secure-the-subscriber.md)   
 [Protéger le serveur de distribution](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [Sécuriser le serveur de publication](../../../relational-databases/replication/security/secure-the-publisher.md)   
 [Afficher et modifier les paramètres de sécurité de la réplication](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  
