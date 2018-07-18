---
title: Créer un rôle d’application | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 31d412581ef160635800d1952fdcd4b19bf05f69
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270435"
---
# <a name="create-an-application-role"></a>Créer un rôle d'application
  Cette rubrique explique comment créer un rôle d'application dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Les rôles d'application limitent l'accès utilisateur à une base de données sauf via des applications spécifiques. Les rôles d'application ne possèdent pas d'utilisateurs, de sorte que la liste **Membres du rôle** n'est pas affichée lorsque l'option **Rôle d'application** est sélectionnée.  
  
> [!IMPORTANT]  
>  La complexité des mots de passe est vérifiée lors de la définition des mots de passe des rôles d'application. Les applications qui appellent des rôles d'application doivent stocker leurs mots de passe. Les mots de passe des rôles d'application doivent toujours être stockés sous forme chiffrée.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer un rôle d'application, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'autorisation ALTER ANY APPLICATION ROLE sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
##### <a name="to-create-an-application-role"></a>Pour créer un rôle d'application  
  
1.  Dans l'Explorateur d'objets, développez la base de données dans laquelle vous souhaitez créer un rôle d'application.  
  
2.  Développez le dossier **Sécurité** .  
  
3.  Développez le dossier **Rôles** .  
  
4.  Cliquez avec le bouton droit sur le dossier **Rôles d’application** et sélectionnez **Nouveau rôle d’application**.  
  
5.  Dans la boîte de dialogue **Rôle d'application - Nouveau** , sur la **Page générale**, entrez le nouveau nom du nouvel rôle d'application dans la zone **Nom du rôle** .  
  
6.  Dans la zone **Schéma par défaut** , spécifiez le schéma qui possédera les objets créés par ce rôle en entrant les noms d'objet. Vous pouvez également cliquer sur les points de suspension **(…)** pour ouvrir la boîte de dialogue **Localiser le schéma** .  
  
7.  Dans la zone **Mot de passe** , entrez un mot de passe pour le nouveau rôle. Entrez à nouveau ce mot de passe dans la zone **Confirmer le mot de passe** .  
  
8.  Sous **Schémas appartenant à ce rôle**, sélectionnez ou affichez les schémas qui appartiendront à ce rôle. Un schéma ne peut appartenir qu'à un seul schéma ou rôle.  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Options supplémentaires  
 La boîte de dialogue **Rôle d'application - Nouveau** offre également des options sur deux pages supplémentaires : **Éléments sécurisables** et **Propriétés étendues**.  
  
-   La page **Éléments sécurisables** répertorie tous les éléments sécurisables possibles et les autorisations sur ces éléments sécurisables qui peuvent être accordées à la connexion.  
  
-   La page **Propriétés étendues** vous permet d'ajouter des propriétés personnalisées aux utilisateurs de base de données.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-an-application-role"></a>Pour créer un rôle d'application  
  
1.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql).  
  
  
