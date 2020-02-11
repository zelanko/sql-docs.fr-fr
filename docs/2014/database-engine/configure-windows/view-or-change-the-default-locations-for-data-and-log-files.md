---
title: Afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 06d17a4feaec0db614f61fb7761b37ea415efc24
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62808709"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a>Afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux (SQL Server Management Studio)
  Cette rubrique explique comment afficher et modifier les emplacements par défaut des nouveaux fichiers de données et fichiers journaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Le chemin d'accès par défaut est obtenu à partir du Registre. Une fois l'emplacement modifié, toutes les nouvelles bases de données créées dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliseront cet emplacement si aucun autre emplacement n'est spécifié.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
-   **Suivi :**  [modification des emplacements par défaut](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
 La bonne pratique pour protéger vos fichiers de données et fichiers journaux consiste à vous assurer qu'ils sont protégés par des listes de contrôle d'accès (ACL). Les listes de contrôle d'accès doivent être définies sur la racine du répertoire où sont créés les fichiers.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a>Pour afficher ou modifier les emplacements par défaut des fichiers de base de données  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans le volet gauche, cliquez sur la page **Paramètres de base de données** .  
  
3.  Dans **Emplacements de la base de données par défaut**, consultez les emplacements par défaut actuels pour les nouveaux fichiers de données et les nouveaux fichiers journaux. Pour modifier un emplacement par défaut, entrez un nouveau chemin d'accès par défaut dans le champ **Données** ou **Journal** , ou cliquez sur le bouton Parcourir pour rechercher et sélectionner un chemin d'accès.  
  
##  <a name="FollowUp"></a>Suivi : après avoir modifié les emplacements par défaut  
 Vous devez arrêter et démarrer le service SQL Server pour valider la modification.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Créer une base de données](../../relational-databases/databases/create-a-database.md)  
  
  
