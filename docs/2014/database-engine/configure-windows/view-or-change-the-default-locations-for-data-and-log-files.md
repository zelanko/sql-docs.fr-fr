---
title: Afficher ou modifier les emplacements par défaut pour les données et les fichiers de journaux (SQL Server Management Studio) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 46bab09c5115781d85fdb3e7c8fc73e6428322fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042974"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a>Afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux (SQL Server Management Studio)
  Cette rubrique explique comment afficher et modifier les emplacements par défaut des nouveaux fichiers de données et fichiers journaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Le chemin d'accès par défaut est obtenu à partir du Registre. Une fois l'emplacement modifié, toutes les nouvelles bases de données créées dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliseront cet emplacement si aucun autre emplacement n'est spécifié.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour afficher ou modifier les données et le journal fichier emplacements par défaut, à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
-   **Suivi :**  [Modification des emplacements par défaut](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
 La bonne pratique pour protéger vos fichiers de données et fichiers journaux consiste à vous assurer qu'ils sont protégés par des listes de contrôle d'accès (ACL). Les listes de contrôle d'accès doivent être définies sur la racine du répertoire où sont créés les fichiers.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a>Pour afficher ou modifier les emplacements par défaut des fichiers de base de données  
  
1.  Dans l'Explorateur d'objets, cliquez avec le bouton droit sur un serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans le volet gauche, cliquez sur la page **Paramètres de base de données** .  
  
3.  Dans **Emplacements de la base de données par défaut**, consultez les emplacements par défaut actuels pour les nouveaux fichiers de données et les nouveaux fichiers journaux. Pour modifier un emplacement par défaut, entrez un nouveau chemin d'accès par défaut dans le champ **Données** ou **Journal** , ou cliquez sur le bouton Parcourir pour rechercher et sélectionner un chemin d'accès.  
  
##  <a name="FollowUp"></a> Suivi : Après avoir modifié les emplacements par défaut  
 Vous devez arrêter et démarrer le service SQL Server pour valider la modification.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Créer une base de données](../../relational-databases/databases/create-a-database.md)  
  
  
