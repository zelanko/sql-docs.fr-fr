---
title: Afficher ou changer les emplacements par défaut des fichiers de données et des fichiers journaux | Microsoft Docs
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6d6a6c9db7e024bd2ac1aee30618c83da054e373
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684787"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>Afficher ou changer les emplacements par défaut des fichiers de données et des fichiers journaux
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
 La bonne pratique pour protéger vos fichiers de données et fichiers journaux consiste à vous assurer qu'ils sont protégés par des listes de contrôle d'accès (ACL). Définissez les listes de contrôle d’accès sur la racine du répertoire où sont créés les fichiers.  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>Afficher ou modifier les emplacements par défaut des fichiers de base de données  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur votre serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans le volet gauche de cette page de propriétés, cliquez sur l’onglet **Paramètres de base de données** .  
  
3.  Dans **Emplacements de la base de données par défaut**, consultez les emplacements par défaut actuels pour les nouveaux fichiers de données et les nouveaux fichiers journaux. Pour modifier un emplacement par défaut, entrez un nouveau chemin d'accès par défaut dans le champ **Données** ou **Journal** , ou cliquez sur le bouton Parcourir pour rechercher et sélectionner un chemin d'accès.  
  
>**REMARQUE :** après avoir modifié les emplacements par défaut, vous devez arrêter et démarrer le service SQL Server pour valider la modification.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Créer une base de données](../../relational-databases/databases/create-a-database.md)  
  
  
