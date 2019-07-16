---
title: Se connecter à Azure SQL DB (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 68fbac69959d423477750a69bb6e5b06ab62af2b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083470"
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Se connecter à Azure SQL DB (SybaseToSQL)
Utilisez la connexion à la boîte de dialogue base de données SQL Azure pour se connecter à la base de données de base de données SQL Azure que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à Azure SQL DB**. Si vous êtes déjà connecté, la commande est **se reconnecter à la base de données SQL Azure.**  
  
## <a name="options"></a>Options  
**Nom de serveur**  
  
Sélectionnez ou entrez le nom du serveur pour la connexion à la base de données SQL Azure.  
  
**Sauvegarde de la base de données**  
  
Sélectionnez, entrez ou **Parcourir** le nom de la base de données.  
  
> [!IMPORTANT]  
> SSMA pour Sybase ne prend pas en charge la connexion à la base de données master dans la base de données SQL Azure.  
  
**Nom d'utilisateur**  
  
Entrez le nom d’utilisateur SSMA utilisera pour se connecter à la base de données de base de données SQL Azure  
  
**Mot de passe**  
  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué.  
  
**Encrypt**  
  
SSMA recommande une connexion chiffrée à la base de données SQL Azure.  
  
## <a name="create-azure-database"></a>Créer une base de données Azure  
S’il n’y a aucune base de données dans le compte de base de données SQL Azure, vous pouvez créer la première base de données.  
  
Pour créer une nouvelle base de données pour la première fois, suivez les étapes suivantes  
  
1.  Cliquez sur le bouton Parcourir qui n’est présent dans la connexion à la boîte de dialogue base de données SQL Azure  
  
2.  S’il n’y a aucune base de données, les éléments de deux menus suivants apparaissent.  
  
    1.  **(aucune base)**  qui est désactivé et grisé de tout le temps  
  
    2.  **Créer la nouvelle base de données** qui est activé uniquement lorsqu’il n’existe aucune base de données sur le compte de base de données SQL Azure. Lorsque vous cliquez sur cet élément de menu, la boîte de dialogue Créer une base de données Azure est présent avec la taille et le nom de la base de données.  
  
3.  Au moment de la création de base de données, les deux paramètres suivants sont fournis comme entrée :  
  
    1.  **Nom de la base de données :** Entrez le nom de la base de données.  
  
    2.  **Taille de la base de données :** Sélectionnez la taille de la base de données dont vous avez besoin pour créer de compte de base de données SQL Azure.  
  
