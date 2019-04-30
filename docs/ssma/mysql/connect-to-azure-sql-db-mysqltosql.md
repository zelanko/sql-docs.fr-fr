---
title: Se connecter à Azure SQL DB (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 81623d27-25af-444f-9779-1edb8c6fb470
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 713a0ba96a2e82f10d4150b337d51f9f1774548f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253145"
---
# <a name="connect-to-azure-sql-db-mysqltosql"></a>Se connecter à Azure SQL DB (MySQLToSQL)
Utilisez la connexion à la boîte de dialogue de SQL Azure pour se connecter à la base de données SQL Azure que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à SQL Azure**. Si vous êtes déjà connecté, la commande est **reconnexion à SQL Azure.**  
  
## <a name="options"></a>Options  
**Nom de serveur**  
  
Sélectionnez ou entrez le nom du serveur pour la connexion à SQL Azure.  
  
**Sauvegarde de la base de données**  
  
Sélectionnez, entrez ou **Parcourir** le nom de la base de données.  
  
> [!IMPORTANT]  
> SSMA pour MySQL ne prend pas en charge la connexion à la base de données master dans SQL Azure.  
  
**Nom d'utilisateur**  
  
Entrez le nom d’utilisateur SSMA utilisera pour se connecter à la base de données SQL Azure  
  
**Mot de passe**  
  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué.  
  
**Encrypt**  
  
SSMA recommande une connexion chiffrée pour SQL Azure.  
  
## <a name="create-azure-database"></a>Créer une base de données Azure  
S’il n’y a aucune base de données dans le compte SQL Azure, vous pouvez créer la première base de données.  
  
Pour créer une nouvelle base de données pour la première fois, suivez les étapes suivantes  
  
1.  Cliquez sur le bouton Parcourir qui n’est présent dans la connexion à la boîte de dialogue de SQL Azure  
  
2.  S’il n’y a aucune base de données, les éléments de deux menus suivants apparaissent.  
  
    1.  **(aucune base)**  qui est désactivé et grisé de tout le temps  
  
    2.  **Créer la nouvelle base de données** qui est activé uniquement lorsqu’il n’existe aucune base de données sur le compte de SQL Azure. Lorsque vous cliquez sur cet élément de menu, la boîte de dialogue Créer une base de données Azure est présent avec la taille et le nom de la base de données.  
  
3.  Au moment de la création de base de données, les deux paramètres suivants sont fournis comme entrée :  
  
    1.  **Nom de la base de données :** Entrez le nom de la base de données.  
  
    2.  **Taille de la base de données :** Sélectionnez la taille de la base de données dont vous avez besoin pour créer dans SQL Azure compte.  
  
