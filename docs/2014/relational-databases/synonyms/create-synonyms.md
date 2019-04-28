---
title: Créer des synonymes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e2a45cf4f34b73996b6ecbd4f9cbb5f5a902e760
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854972"
---
# <a name="create-synonyms"></a>Créer des synonymes
  Cette rubrique explique comment créer un synonyme dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer un synonyme à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour créer un synonyme dans un schéma donné, un utilisateur doit disposer de l'autorisation CREATE SYNONYM, et il doit posséder le schéma ou bénéficier de l'autorisation ALTER SCHEMA. L'autorisation CREATE SYNONYM est octroyable.  
  
####  <a name="Permissions"></a> Autorisations  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-synonym"></a>Pour créer un synonyme  
  
1.  Dans l' **Explorateur d'objets**, développez la base de données dans laquelle vous souhaitez créer votre nouvelle vue.  
  
2.  Cliquez avec le bouton droit sur le dossier **Synonymes**, puis cliquez sur **Nouveau synonyme...**.  
  
3.  Dans la boîte de dialogue **Ajouter un synonyme** , entrez les informations suivantes.  
  
     **Nom du synonyme**  
     Tapez le nouveau nom à utiliser pour cet objet.  
  
     **Schéma du synonyme**  
     Tapez le schéma du nouveau nom à utiliser pour cet objet.  
  
     **Nom du serveur**  
     Tapez l'instance de serveur à laquelle vous connecter.  
  
     **Nom de la base de données**  
     Tapez ou sélectionnez la base de données contenant l'objet.  
  
     **Schéma**  
     Tapez ou sélectionnez le schéma propriétaire de l'objet.  
  
     **Type d'objet**  
     Permet de sélectionner le type d'objet.  
  
     **Nom de l'objet**  
     Tapez le nom de l'objet auquel le synonyme fait référence.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-synonym"></a>Pour créer un synonyme  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 L'exemple suivant crée un synonyme pour une table existante dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Le synonyme est ensuite utilisé dans les exemples suivants.  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 L'exemple suivant insère une ligne dans la table de base référencée par le synonyme `MyAddressType` .  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 L'exemple suivant montre comment un synonyme peut être référencé en SQL dynamique.  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
