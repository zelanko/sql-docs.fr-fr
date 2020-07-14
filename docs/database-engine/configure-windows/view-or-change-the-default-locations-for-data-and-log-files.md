---
title: Afficher ou changer les emplacements par défaut des fichiers de données et des fichiers journaux | Microsoft Docs
description: Découvrez comment afficher ou modifier les emplacements par défaut des fichiers de données et des fichiers journaux SQL Server. Découvrez comment protéger les fichiers avec des listes de contrôle d’accès (ACL).
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9a0c720684f0eefa301e9a5387ffda54e349f85d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680786"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>Afficher ou changer les emplacements par défaut des fichiers de données et des fichiers journaux
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
 La bonne pratique pour protéger vos fichiers de données et fichiers journaux consiste à vous assurer qu'ils sont protégés par des listes de contrôle d'accès (ACL). Définissez les listes de contrôle d’accès sur la racine du répertoire où sont créés les fichiers.  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>Afficher ou modifier les emplacements par défaut des fichiers de base de données  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur votre serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans le volet gauche de cette page de propriétés, cliquez sur l’onglet **Paramètres de base de données** .  
  
3.  Dans **Emplacements de la base de données par défaut**, consultez les emplacements par défaut actuels pour les nouveaux fichiers de données et les nouveaux fichiers journaux. Pour modifier un emplacement par défaut, entrez un nouveau chemin d'accès par défaut dans le champ **Données** ou **Journal** , ou cliquez sur le bouton Parcourir pour rechercher et sélectionner un chemin d'accès.  
  
>**REMARQUE :** Après avoir modifié les emplacements par défaut, vous devez arrêter et démarrer le service SQL Server pour valider la modification.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Créer une base de données](../../relational-databases/databases/create-a-database.md)  
  
  
