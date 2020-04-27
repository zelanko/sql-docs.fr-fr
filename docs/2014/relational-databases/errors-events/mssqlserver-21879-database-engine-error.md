---
title: MSSQLSERVER_21879 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21879 (Database Engine error)
ms.assetid: fcfab735-05ca-423a-89f1-fdee7e2ed8c0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 98bfedce41d05a613fe47941b86cfa3fa176ee5d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62869176"
---
# <a name="mssqlserver_21879"></a>MSSQLSERVER_21879
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|21879|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21879|  
|Texte du message|Impossible d'interroger le serveur redirigé '%s' pour le serveur de publication d'origine '%s' et la base de données du serveur de publication '%s' pour déterminer le nom du serveur distant ; erreur %d, message d'erreur '%s'.|  
  
## <a name="explanation"></a>Explication  
 `sp_validate_redirected_publisher` utilise un serveur lié temporaire créé pour se connecter au serveur de publication redirigé afin de découvrir le nom du serveur distant. L'erreur 21879 est retournée lorsque la requête de serveur lié échoue. L'appel pour demander le nom du serveur distant est généralement la première utilisation qui est faite du serveur lié temporaire, donc si des problèmes de connectivité existent, ils sont susceptibles d'apparaître d'abord lors de cet appel. Cet appel exécute simplement `@@servername` sur le serveur distant.  
  
 Le serveur lié utilisé pour interroger le serveur de publication redirigé utilise le mode, la connexion et le mot de passe de sécurité fournis lorsque `sp_adddistpublisher` a été appelé pour le serveur de publication d'origine.  
  
-   Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été utilisée (mode de sécurité 0), alors la connexion et le mot de passe spécifiés sont utilisés pour la connexion au serveur distant.  
  
-   Si l'authentification Windows a été utilisée (mode de sécurité 1) une connexion approuvée est utilisée pour la connexion.  
  
    -   Si `sp_validate_redirected_publisher` est appelé explicitement par un utilisateur, la connexion Windows sous laquelle l'utilisateur s'exécute est utilisée pour la connexion.  
  
    -   Si le serveur de publication `sp_validate_redirected_` est appelé par un agent de réplication à partir de `sp_get_redirected_publisher`, la connexion Windows associée à l'agent est utilisée.  
  
 L'erreur 21879 peut indiquer que' `sp_validate_redirected_publisher` a été appelé à l'aide d'une connexion qui n'est pas connue sur le serveur de publication cible redirigé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que la connexion d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la connexion via l'authentification Windows, est valide sur tous les réplicas de groupe de disponibilité et possède des autorisations suffisantes pour accéder aux tables de métadonnées d'abonnement (syssubscriptions et sysmergesubscriptions) dans la base de données du serveur de publication.  
  
 Il existe des considérations spéciales lorsque l'erreur 21879 est retournée d'un appel à `sp_get_redirected_publisher` initié par un agent de réplication s'exécutant sur un nœud autre que le serveur de distribution ; comme un agent de fusion s'exécutant sur un abonné. Si l'authentification Windows est utilisée pour la connexion au serveur de publication redirigé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être configuré pour l'authentification Kerberos afin que connexion soit établie avec succès. Lorsque l'authentification Windows est utilisée et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas configuré pour l'authentification Kerberos, l'erreur 18456 indiquant que la connexion 'NT AUTHORITY\ANONYMOUS LOGON' a échoué est reçue par un agent de fusion s'exécutant sur un abonné. Il existe trois moyens possibles de résoudre ce problème :  
  
-   Configurez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l'authentification Kerberos. Consultez **Authentification Kerberos et SQL Server** dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Utilisez `sp_changedistpublisher` pour modifier le mode de sécurité associé au serveur de publication d’origine dans MSdistpublishers, ainsi que pour spécifier une connexion et un mot de passe à utiliser pour la connexion.  
  
-   Spécifiez le paramètre de ligne de commande *BypassPublisherValidation* sur la ligne de commande de l' `sp_get_redirected_publisher` agent de fusion pour ignorer la validation lorsque est appelé sur le serveur de distribution.  
  
  
