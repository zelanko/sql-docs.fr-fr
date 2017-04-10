---
title: "G&#233;rer des connexions dans la liste d&#39;acc&#232;s &#224; la publication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "logins [SQL Server replication], publication access list"
  - "publications [SQL Server replication], publication access lists"
  - "publication access list (PAL)"
  - "PAL (publication access list)"
  - "connexions [réplication SQL Server], gestion"
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# G&#233;rer des connexions dans la liste d&#39;acc&#232;s &#224; la publication
  Cette rubrique explique comment gérer des connexions dans la liste d'accès à la publication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. L'accès à une publication est contrôlé par la liste d'accès à la publication. Les connexions et les groupes peuvent être ajoutés et supprimés de la liste d'accès à la publication.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Conditions préalables](#Prerequisites)  
  
-   **Pour gérer les connexions dans la liste d'accès à la publication, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez associer la connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à un utilisateur de base de données dans la base de données de publication avant d'ajouter cette connexion à la liste d'accès à la publication.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Vous utilisez la liste d’accès (aux publications PAL) sur le **liste d’accès** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue pour gérer les connexions. Pour plus d’informations sur la façon d’accéder à cette boîte de dialogue, consultez [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour gérer des noms de connexion dans la liste d'accès à la publication  
  
1.  Sur le **liste d’accès** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, utilisez le **Ajouter**, **Supprimer**, et **Supprimer tous les** boutons pour ajouter et supprimer des connexions et des groupes à partir de la publication. Ne supprimez pas **distributor_admin** à partir de la publication. Ce compte est utilisé par la réplication.  
  
    > [!NOTE]  
    >  En cas d'utilisation d'un serveur de distribution distant, les comptes de la liste d'accès à la publication doivent être disponibles à la fois auprès du serveur de publication et auprès du serveur de distribution. Le compte doit être un compte de domaine ou un compte local défini sur les deux serveurs. Les mots de passe associés aux deux connexions doivent être identiques.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher les groupes et les connexions qui figurent dans la liste d'accès à la publication  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_help_publication_access](../../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md). Spécifiez le nom de la publication pour **@publication**. Cela affiche des informations sur les groupes et les connexions qui figurent dans la liste d'accès à la publication.  
  
#### Pour ajouter des groupes et des connexions dans la liste d'accès à la publication  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_grant_publication_access](../../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md). Spécifiez le nom de la publication pour **@publication**et le nom de la connexion ou du groupe à ajouter pour **@login**.  
  
#### Pour supprimer des groupes et des connexions de la liste d'accès à la publication  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_revoke_publication_access](../../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md). Spécifiez le nom de la publication pour **@publication**et le nom de la connexion ou du groupe à supprimer pour **@login**.  
  
## Voir aussi  
 [Manage Logins in the Publication Access List](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)   
 [Modèle de sécurité de l'Agent de réplication](../../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Sécuriser une topologie de réplication](../../../relational-databases/replication/security/secure-a-replication-topology.md)   
 [Sécuriser le serveur de publication](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  