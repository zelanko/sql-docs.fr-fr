---
title: "Se connecter à la base de données SQL Azure (MySQLToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 81623d27-25af-444f-9779-1edb8c6fb470
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 98888517c8f092b5d014be0bf2c0112f1afa1629
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-azure-sql-db-mysqltosql"></a>Se connecter à la base de données SQL Azure (MySQLToSQL)
Utilisez la connexion à la boîte de dialogue SQL Azure pour se connecter à la base de données SQL Azure que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à SQL Azure**. Si vous êtes déjà connecté, la commande est **se reconnecter à SQL Azure.**  
  
## <a name="options"></a>Options  
**Nom de serveur**  
  
Sélectionnez ou entrez le nom du serveur pour se connecter à SQL Azure.  
  
**Base de données**  
  
Sélectionnez, entrez ou **Parcourir** le nom de la base de données.  
  
> [!IMPORTANT]  
> SSMA pour MySQL ne prend pas en charge la connexion à la base de données master dans SQL Azure.  
  
**Nom d'utilisateur**  
  
Entrez le nom d’utilisateur SSMA utilisera pour se connecter à la base de données SQL Azure  
  
**Mot de passe**  
  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué.  
  
**Chiffrer**  
  
SSMA recommande une connexion chiffrée pour SQL Azure.  
  
## <a name="create-azure-database"></a>Créer une base de données Azure  
S’il n’y a aucune base de données dans le compte SQL Azure, vous pouvez créer la première base de données.  
  
Pour créer une nouvelle base de données pour la première fois, suivez les étapes suivantes  
  
1.  Cliquez sur le bouton Parcourir qui est présent dans la connexion à la boîte de dialogue SQL Azure  
  
2.  S’il n’y a aucune base de données, les deux options suivantes s’affichent.  
  
    1.  **(bases de données introuvables) ** qui est désactivé et grisé tout le temps  
  
    2.  **Créer la nouvelle base de données** qui est activé uniquement lorsqu’il n’y aucune base de données sur le compte SQL Azure. Lorsque vous cliquez sur cet élément de menu, la boîte de dialogue Créer une base de données Azure est présent avec la taille et le nom de la base de données.  
  
3.  Au moment de la création de la base de données, les deux paramètres suivants figurent en tant qu’entrée :  
  
    1.  **Nom de la base de données :** Entrez le nom de la base de données.  
  
    2.  **Taille de la base de données :** sélectionner la taille de la base de données dont vous avez besoin pour créer de compte SQL Azure.  
  

