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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68083470"
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Se connecter à Azure SQL DB (SybaseToSQL)
Utilisez la boîte de dialogue se connecter à la base de données SQL Azure pour vous connecter à la base de données SQL Azure que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le menu **fichier** , sélectionnez **se connecter à Azure SQL DB**. Si vous vous êtes connecté précédemment, la commande se **reconnecte à Azure SQL db.**  
  
## <a name="options"></a>Options  
**Nom du serveur**  
  
Sélectionnez ou entrez le nom du serveur pour la connexion à Azure SQL DB.  
  
**Sauvegarde de la base de données**  
  
Sélectionnez, entrez ou **recherchez** le nom de la base de données.  
  
> [!IMPORTANT]  
> SSMA pour Sybase ne prend pas en charge la connexion à la base de données Master dans Azure SQL DB.  
  
**Nom d'utilisateur**  
  
Entrez le nom d’utilisateur que SSMA utilisera pour se connecter à la base de données Azure SQL DB  
  
**Mot de passe**  
  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué.  
  
**Encrypt**  
  
SSMA recommande la connexion chiffrée à Azure SQL DB.  
  
## <a name="create-azure-database"></a>Créer une base de données Azure  
S’il n’existe aucune base de données dans le compte Azure SQL DB, vous pouvez créer la toute première base de données.  
  
Pour créer une base de données pour la première fois, procédez comme suit :  
  
1.  Cliquez sur le bouton Parcourir qui est présent dans la boîte de dialogue Connexion à Azure SQL DB.  
  
2.  S’il n’y a aucune base de données, les deux éléments de menu suivants s’affichent.  
  
    1.  **(aucune base de données trouvée)** qui est désactivée et grisée tout le temps  
  
    2.  **Créer une nouvelle base de données** qui est activée uniquement lorsqu’il n’existe aucune base de données sur le compte Azure SQL db. Lorsque vous cliquez sur cet élément de menu, la boîte de dialogue créer une base de données Azure est présente avec le nom et la taille de la base de données.  
  
3.  Au moment de la création de la base de données, les deux paramètres suivants sont fournis comme entrée :  
  
    1.  **Nom de la base de données :** Entrez le nom de la base de données.  
  
    2.  **Taille de la base de données :** Sélectionnez la taille de base de données que vous devez créer dans le compte Azure SQL DB.  
  
