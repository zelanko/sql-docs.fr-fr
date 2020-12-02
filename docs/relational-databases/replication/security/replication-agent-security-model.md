---
title: Modèle de sécurité de l’Agent de réplication | Microsoft Docs
description: Dans SQL Server, le modèle de sécurité de l’Agent de réplication permet un contrôle fin des comptes sous lesquels les agents de réplication s’exécutent et établissent des connexions.
ms.custom: ''
ms.date: 04/26/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, security
- agents [SQL Server replication], security
- Distribution Agent, security
- logins [SQL Server replication], permissions for agents
- security [SQL Server replication], agent security model
- Log Reader Agent, security
- Queue Reader Agent, security
- Merge Agent, security
- replication [SQL Server], agents and profiles
ms.assetid: 6d09fc8d-843a-4a7a-9812-f093d99d8192
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 41d77ae1b9c0763fedf2e53610bb3a0be5cd185c
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "87823924"
---
# <a name="replication-agent-security-model"></a>Modèle de sécurité de l'Agent de réplication
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Le modèle de sécurité de l’agent de réplication permet un contrôle fin des comptes sous lesquels les agents de réplication s’exécutent et établissent des connexions : un compte distinct peut être spécifié pour chaque agent. Pour plus d’informations sur la manière de spécifier des comptes, consultez [Identité et contrôle d’accès pour la réplication](../../../relational-databases/replication/security/identity-and-access-control-replication.md).  

Le modèle de sécurité de l’agent de réplication est un peu différent pour Azure SQL Managed Instance, car il n’y a aucun compte Windows sous lequel les agents s’exécuteront. Au lieu de cela, tout doit être effectué par le biais de l’authentification SQL Server. 
  
> [!IMPORTANT]  
>  Lorsqu'un membre du rôle serveur fixe **sysadmin** configure la réplication, les agents de réplication peuvent être configurés pour emprunter l'identité du compte de l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Il suffit de ne pas spécifier de nom de connexion et de mot de passe pour un Agent de réplication ; toutefois, cette méthode n'est pas recommandée. Pour des raisons de sécurité, il est plutôt recommandé de spécifier un compte pour chaque agent, disposant des autorisations minimales décrites dans la section « Autorisations requises par les agents » plus loin dans cette rubrique.  
  
 Comme tous les exécutables, les agents de réplication sont exécutés dans le contexte d'un compte Windows. Les agents établissent des connexions de sécurité intégrée Windows en utilisant ces comptes. Le compte sous lequel l'agent s'exécute dépend de la manière dont l'agent est démarré :  
  
-   Démarrage de l’agent à partir d’un travail de l’Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (par défaut) : quand un travail de l’Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sert à démarrer un agent de réplication, l’agent s’exécute dans le contexte d’un compte que vous spécifiez lors de la configuration de la réplication. Pour plus d'informations sur l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et la réplication, consultez la section « Sécurité de l'Agent sous l'Agent SQL Server » plus loin dans cette rubrique. Pour plus d’informations sur les autorisations requises pour le compte sous lequel s’exécute l’Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [Configurer l’Agent SQL Server](../../../ssms/agent/configure-sql-server-agent.md).  
  
-   Démarrage de l’agent à partir d’une ligne de commande MS-DOS, directement ou par le biais d’un script : l’agent s’exécute dans le contexte du compte de l’utilisateur exécutant l’agent sur la ligne de commande.  
  
-   Démarrage de l’agent à partir d’une application qui utilise des objets RMO (Replication Management Objects) ou un contrôle ActiveX : l’agent s’exécute dans le contexte de l’application appelant RMO ou le contrôle ActiveX.  
  
    > [!NOTE]  
    >  Les contrôles ActiveX sont déconseillés.  
  
 Il est recommandé d'établir les connexions dans le contexte de sécurité intégrée Windows. Pour des besoins de compatibilité descendante, la sécurité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut également être utilisée. Pour plus d'informations sur les meilleures pratiques, consultez [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="permissions-that-are-required-by-agents"></a>Autorisations requises par les agents  
 Les comptes sous lesquels les agents s'exécutent et établissent des connexions nécessitent différentes autorisations. Ces autorisations sont décrites dans le tableau suivant. Il est recommandé d'exécuter chaque agent sous un compte Windows différent et d'accorder au compte uniquement les autorisations nécessaires. Pour obtenir des informations sur la liste d’accès à la publication (PAL, Publication Access List), qui concerne un certain nombre d’agents, consultez [Sécuriser le serveur de publication](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
> [!NOTE]  
>  La fonctionnalité Contrôle de compte d'utilisateur dans certains systèmes d'exploitation Windows peut empêcher l'accès administratif au partage de fichiers d'instantanés. Vous devez donc octroyer explicitement des autorisations sur le partage de fichiers d'instantanés aux comptes Windows qui sont utilisés par l'Agent d'instantané, l'Agent de distribution et l'Agent de fusion. Vous devez effectuer cette opération même si les comptes Windows sont membres du groupe Administrateurs. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
|Agent|Autorisations|  
|-----------|-----------------|  
|Agent d'instantané|Le compte Windows sous lequel s'exécute l'agent est utilisé pour se connecter au serveur de distribution. Ce compte doit obligatoirement :<br /><br /> \- être au moins membre du rôle de base de données fixe **db_owner** dans la base de données de distribution ;<br /><br /> \- disposer des autorisations de lecture, écriture et modification sur le partage de fichiers d’instantanés.<br /><br /> <br /><br /> Notez que le compte utilisé pour *se connecter* au serveur de publication doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données de publication.|  
|l'Agent de lecture du journal ;|Le compte Windows sous lequel s'exécute l'agent est utilisé pour se connecter au serveur de distribution. Ce compte doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données de distribution.<br /><br /> Le compte utilisé pour se connecter au serveur de publication doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données de publication.<br /><br /> Lors de la sélection des options **sync_type** , *replication support only*, *initialize with backup* ou *initialize from lsn*, l'Agent de lecture du journal doit s'exécuter après l'exécution de **sp_addsubscription**, afin que les scripts d'installation soient écrits dans la base de données de distribution. L'Agent de lecture du journal doit s'exécuter sous un compte membre du rôle serveur fixe **sysadmin** . Lorsque l'option **sync_type** a la valeur *Automatic*, aucune action particulière de l'Agent de lecture du journal n'est requise.|  
|Agent de distribution pour un abonnement par envoi de données (push)|Le compte Windows sous lequel s'exécute l'agent est utilisé pour se connecter au serveur de distribution. Ce compte doit obligatoirement :<br /><br /> \- être au moins membre du rôle de base de données fixe **db_owner** dans la base de données de distribution ;<br /><br /> \- être membre de la liste d’accès à la publication (PAL) ;<br /><br /> \- avoir les autorisations de lecture sur le partage des fichiers d’instantanés ;<br /><br /> \- avoir les autorisations de lecture sur le répertoire d’installation du fournisseur OLE DB pour l’Abonné si l’abonnement est destiné à un Abonné non-SQL Server.<br /><br /> \- Lors de la réplication des données LOB, l’agent de distribution doit avoir des autorisations en écriture sur la réplication **C:\Program Files\Microsoft SQL Server\XX\COMfolder** , où XX représente l’ID d’instance.<br /><br /> <br /><br /> Notez que le compte employé pour *se connecter* à l’Abonné doit au moins être membre du rôle de base de données fixe **db_owner** dans la base de données d’abonnement, ou bien disposer d’autorisations équivalentes si l’abonnement s’adresse à un Abonné non-SQL Server.<br /><br /> Notez également que, lorsque vous utilisez `-subscriptionstreams >= 2` sur l’agent de distribution, vous devez également accorder l’autorisation **View Server State** sur les abonnés pour détecter les blocages.|  
|Agent de distribution pour un abonnement par extraction de données (pull)|Le compte Windows sous lequel s'exécute l'agent est utilisé pour se connecter à l'Abonné. Ce compte doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données d'abonnement. Le compte servant à se connecter au serveur de distribution doit obligatoirement :<br /><br /> \- être membre de la liste d’accès à la publication (PAL) ;<br /><br /> \- avoir les autorisations de lecture sur le partage des fichiers d’instantanés ;<br /><br /> \- Lors de la réplication des données LOB, l’agent de distribution doit avoir des autorisations en écriture sur la réplication **C:\Program Files\Microsoft SQL Server\XX\COMfolder** , où XX représente l’ID d’instance.<br /><br /> <br /><br /> Notez que, lorsque vous utilisez `-subscriptionstreams >= 2` sur l’agent de distribution, vous devez également accorder l’autorisation **View Server State** sur les abonnés pour détecter les blocages.|  
|Agent de fusion pour un abonnement par envoi de données (push)|Le compte Windows sous lequel s'exécute l'agent est utilisé pour se connecter au serveur de publication et au serveur de distribution. Ce compte doit obligatoirement :<br /><br /> \- être au moins membre du rôle de base de données fixe **db_owner** dans la base de données de distribution ;<br /><br /> \- être membre de la liste d’accès à la publication (PAL) ;<br /><br /> \- Être un compte de connexion associé à un utilisateur ayant des autorisations de lecture-écriture dans la base de données de publication.<br /><br /> \- avoir les autorisations de lecture sur le partage des fichiers d’instantanés ;<br /><br /> <br /><br /> Notez que le compte utilisé pour *se connecter* à l’Abonné doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données d'abonnement.|  
|Agent de fusion pour un abonnement par extraction de données (pull)|Le compte Windows sous lequel s'exécute l'agent est utilisé pour se connecter à l'Abonné. Ce compte doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données d'abonnement. Le compte servant à se connecter au serveur de publication et au serveur de distribution doit obligatoirement :<br /><br /> \- être membre de la liste d’accès à la publication (PAL) ;<br /><br /> \- Être un compte de connexion associé à un utilisateur ayant des autorisations de lecture-écriture dans la base de données de publication.<br /><br /> \- être un compte de connexion associé à un utilisateur enregistré dans la base de données de distribution. l'utilisateur peut être un **Guest** ;<br /><br /> \- avoir les autorisations de lecture sur le partage des fichiers d’instantanés ;|  
|Agent de lecture de la file d'attente|Le compte Windows sous lequel s'exécute l'agent est utilisé pour se connecter au serveur de distribution. Ce compte doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données de distribution.<br /><br /> Le compte utilisé pour se connecter au serveur de publication doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données de publication.<br /><br /> Le compte utilisé pour se connecter à l'Abonné doit être au minimum membre du rôle de base de données fixe **db_owner** dans la base de données d'abonnement.|  
  
## <a name="agent-security-under-sql-server-agent"></a>Sécurité de l'Agent dans l'Agent SQL Server  
 Lorsque vous configurez la réplication à l'aide de procédures [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou RMO, un travail de l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est créé par défaut pour chaque agent. Les agents s'exécutent ensuite dans le contexte d'une étape de travail, qu'ils s'exécutent en continu, dans le cadre d'une planification ou à la demande. Vous pouvez afficher ces travaux dans le dossier **Jobs** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Le tableau suivant donne la liste des noms des travaux.  
  
|Agent|Nom du travail|  
|-----------|--------------|  
|Agent d'instantané|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<integer>**|  
|Agent d'instantané pour une partition de publication de fusion|**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**|  
|l'Agent de lecture du journal ;|**\<Publisher>-\<PublicationDatabase>-\<integer>**|  
|Agent de fusion pour les abonnements extraits|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|  
|Agent de fusion pour abonnements par envoi de données (push)|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|Agent de distribution pour abonnements par envoi de données (push)|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|Agent de distribution pour abonnements par extraction de données (pull)|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>**|  
|Agent de distribution pour les abonnements par envoi de données aux Abonnés non SQL Server|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|Agent de lecture de la file d'attente|**[\<Distributor>].\<integer>**|  
  
 \*Pour les abonnements par émission de données aux publications Oracle, le nom du travail est **\<Publisher>-\<Publisher**> au lieu de **\<Publisher>-\<PublicationDatabase>** .  
  
 \*\*Pour les abonnements par extraction aux publications Oracle, le nom du travail est **\<Publisher>-\<DistributionDatabase**> au lieu de **\<Publisher>-\<PublicationDatabase>** .  
  
 Lorsque vous configurez la réplication, vous spécifiez les comptes sous lesquels les agents doivent être exécutés. Cependant, toutes les étapes de travail s'exécutent dans le contexte de sécurité d'un *proxy*; la réplication effectue donc les mappages suivants en interne pour les comptes d'agent spécifiés :  
  
-   Le compte est d’abord mappé à des informations d’identification à l’aide de l’instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] [CREATE CREDENTIAL](../../../t-sql/statements/create-credential-transact-sql.md). Les proxys de l'Agent[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisent les informations d'identification pour stocker les informations relatives aux comptes d'utilisateur Windows.  
  
-   La procédure stockée [sp_add_proxy](../../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md) est appelée et les informations d'identification sont utilisées pour créer un proxy.  
  
> [!NOTE]  
>  Ces informations sont fournies pour vous aider à comprendre les conséquences de l'exécution d'agents dans le contexte de sécurité approprié. Il ne devrait pas être nécessaire d'interagir directement avec les informations d'identification ou les proxys qui ont été créés.  
  
## <a name="see-also"></a>Voir aussi  
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Afficher et modifier les paramètres de sécurité de la réplication](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Sécuriser le dossier d’instantanés](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
