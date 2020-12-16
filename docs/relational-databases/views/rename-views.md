---
description: Renommer des vues
title: Renommer des vues | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 14936117fe2e9267a2ebb818a102d1245548e073
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97425478"
---
# <a name="rename-views"></a>Renommer des vues
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]
  Vous pouvez renommer une vue dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  Si vous renommez une vue, l'exécution du code et des applications qui en dépendent peut échouer. Il peut s'agir d'autres vues, de requêtes, de procédures stockées, de fonctions définies par l'utilisateur et d'applications clientes. Notez que ces défaillances se produisent en cascade.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Composants requis](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour renommer une vue, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After renaming a view](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Obtenez une liste de toutes les dépendances sur la vue. Tous les objets, scripts ou applications qui font référence à la vue doivent être modifiés pour refléter le nouveau nom de la vue. Pour plus d'informations, consultez [Get Information About a View](../../relational-databases/views/get-information-about-a-view.md). Nous vous recommandons de supprimer la vue et de la recréer sous un nouveau nom plutôt que de la renommer. En recréant la vue, vous mettez à jour les informations de dépendance pour les objets référencés dans la vue.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert l'autorisation ALTER sur SCHEMA, l'autorisation CONTROL sur OBJECT et l'autorisation CREATE VIEW sur la base de données.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>Pour renommer une vue  
  
1.  Dans l' **Explorateur d'objets**, développez la base de données qui contient la vue que vous souhaitez renommer et le dossier **Vue** .  
  
2.  Cliquez avec le bouton droit sur la vue que vous souhaitez renommer et sélectionnez **Renommer**.  
  
3.  Entrez le nouveau nom de la vue.  

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour renommer une vue**  
  
 Même si vous pouvez utiliser **sp_rename** pour modifier le nom de la vue, nous vous recommandons de supprimer la vue existante puis de la recréer sous le nouveau nom.  
  
 Pour plus d’informations, consultez [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md) et [DROP VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/drop-view-transact-sql.md).  
  
##  <a name="follow-up-after-renaming-a-view"></a><a name="FollowUp"></a> Suivi : Après avoir renommé une vue  
 Vérifiez que tous les objets, scripts et applications qui font référence à l’ancien nom de la vue utilisent désormais le nouveau nom.  
  
  
