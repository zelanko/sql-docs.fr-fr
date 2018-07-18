---
title: Gérer des utilisateurs DQS dans SSMS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
caps.latest.revision: 10
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 949c86f3a83856a474a388bf94f224d5a6273174
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306059"
---
# <a name="manage-dqs-users-in-ssms"></a>Gérer des utilisateurs DQS dans SSMS
  Cette rubrique décrit comment créer des utilisateurs supplémentaires dans l'instance SQL Server à l'aide de SQL Server Management Studio et leur accorder des rôles [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) appropriés sur la base de données DQS_MAIN.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Votre compte d'utilisateur Windows doit être un membre du rôle serveur fixe approprié (tel que securityadmin, serveradmin ou sysadmin) pour créer une connexion SQL et lui accorder des rôles DQS appropriés.  
  
##  <a name="GrantRoles"></a> Créer une connexion SQL et l’accorder un rôle DQS  
  
1.  Démarrez Microsoft SQL Server Management Studio.  
  
2.  Dans Microsoft SQL Server Management Studio, développez votre instance SQL Server, puis développez **Sécurité**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Sécurité** , pointez sur **Nouveau**, puis cliquez sur **Connexion**.  
  
4.  Dans la boîte de dialogue **Nouvelle connexion** , spécifiez le nom d'un utilisateur Windows dans la zone **Nom de connexion** , spécifiez le type d'authentification **Authentification Windows**et cliquez sur **Rechercher** pour valider l'utilisateur.  
  
    > [!NOTE]  
    >  DQS prend en charge uniquement l'authentification Windows ; l'authentification SQL Server n'est pas prise en charge.  
  
5.  Une fois l'utilisateur validé, dans le volet de gauche, cliquez sur **Mappage de l'utilisateur** .  
  
6.  Dans le volet droit, activez la case à cocher sous la colonne de **Mappage** pour la base de données **DQS_MAIN** , puis sélectionnez la case à cocher **dqs_administrator**, **dqs_kb_editor**ou **dqs_kb_operator** dans le volet **Appartenance au rôle de base de données : DQS_MAIN** , selon le niveau d'accès nécessaire pour l'utilisateur.  
  
7.  Dans la boîte de dialogue **Nouvelle connexion** , cliquez sur **OK** pour appliquer les modifications.  
  
    > [!NOTE]  
    >  Si vous accordez le rôle **dqs_administrator** à un utilisateur, appliquez les modifications, puis revérifiez les autorisations utilisateur ; les deux autres cases à cocher de rôles DQS (**dq_kb_editor** et **dqs_kb_operator**) sont également activées.  
  
  
