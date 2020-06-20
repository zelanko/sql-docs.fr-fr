---
title: Gérer des connexions dans la liste d’accès à la publication | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication], publication access list
- publications [SQL Server replication], publication access lists
- publication access list (PAL)
- PAL (publication access list)
- logins [SQL Server replication], managing
ms.assetid: fceb216b-0b18-4e3b-8ae0-13e35920dcbc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b96e6f46403cf3a482f00a3f5155527177920967
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85009911"
---
# <a name="manage-logins-in-the-publication-access-list"></a>Gérer des connexions dans la liste d'accès à la publication
  Cette rubrique explique comment gérer des connexions dans la liste d'accès à la publication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. L'accès à une publication est contrôlé par la liste d'accès à la publication. Les connexions et les groupes peuvent être ajoutés et supprimés de la liste d'accès à la publication.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Prérequis](#Prerequisites)  
  
-   **Pour gérer les connexions dans la liste d'accès à la publication, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez associer la connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à un utilisateur de base de données dans la base de données de publication avant d'ajouter cette connexion à la liste d'accès à la publication.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Vous utilisez la liste d’accès à la publication (PAL) dans la page **liste d’accès** à la publication de la boîte de dialogue Propriétés de la **publication- \<Publication> ** pour gérer les connexions. Pour plus d’informations sur la façon d’accéder à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’une publication](../publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-manage-logins-in-the-pal"></a>Pour gérer des noms de connexion dans la liste d'accès à la publication  
  
1.  Dans la page Liste d’accès à la publication de la boîte de dialogue Propriétés de la **publication- \<Publication> ** , utilisez les boutons **Ajouter**, **supprimer**et **Supprimer tout** pour ajouter et supprimer des connexions et des groupes de la **liste d’accès** aux publications. Ne supprimez pas **distributor_admin** de la liste d'accès à la publication. Ce compte est utilisé par la réplication.  
  
    > [!NOTE]  
    >  En cas d'utilisation d'un serveur de distribution distant, les comptes de la liste d'accès à la publication doivent être disponibles à la fois auprès du serveur de publication et auprès du serveur de distribution. Le compte doit être un compte de domaine ou un compte local défini sur les deux serveurs. Les mots de passe associés aux deux connexions doivent être identiques.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-groups-and-logins-that-belong-to-the-pal"></a>Pour afficher les groupes et les connexions qui figurent dans la liste d'accès à la publication  
  
1.  Exécutez [sp_help_publication_access](/sql/relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql)sur la base de données de publication du serveur de publication. Pour ** \@ publication**, spécifiez le nom de la publication. Cela affiche des informations sur les groupes et les connexions qui figurent dans la liste d'accès à la publication.  
  
#### <a name="to-add-groups-and-logins-to-the-pal"></a>Pour ajouter des groupes et des connexions dans la liste d'accès à la publication  
  
1.  Exécutez [sp_grant_publication_access](/sql/relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql)sur la base de données de publication du serveur de publication. Pour ** \@ publication**, spécifiez le nom de la publication et, pour la ** \@ connexion**, spécifiez le nom de la connexion ou du groupe à ajouter.  
  
#### <a name="to-remove-groups-and-logins-from-the-pal"></a>Pour supprimer des groupes et des connexions de la liste d'accès à la publication  
  
1.  Exécutez [sp_revoke_publication_access](/sql/relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql)sur la base de données de publication du serveur de publication. Pour ** \@ publication**, spécifiez le nom de la publication et, pour la ** \@ connexion**, spécifiez le nom de la connexion ou du groupe en cours de suppression.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de sécurité de l’agent de réplication](replication-agent-security-model.md)   
 [Sécuriser une topologie de réplication](view-and-modify-replication-security-settings.md)   
 [Sécuriser le serveur de publication](secure-the-publisher.md)  
  
  
