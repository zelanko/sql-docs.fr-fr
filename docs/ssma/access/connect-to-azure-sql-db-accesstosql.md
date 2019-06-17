---
title: Se connecter à Azure SQL DB (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 57a745385de80a3040897310ddc5b43b1301ea86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63138753"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Se connecter à Azure SQL DB (AccessToSQL)
Utilisez la connexion à la boîte de dialogue de SQL Azure pour se connecter à la base de données SQL Azure que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à SQL Azure**. Si vous êtes déjà connecté, la commande est **reconnexion à SQL Azure.**  
  
## <a name="options"></a>Options  
**Nom de serveur**  
  
Sélectionnez ou entrez le nom du serveur pour la connexion à SQL Azure.  
  
**Sauvegarde de la base de données**  
  
Sélectionnez, entrez ou **Parcourir** le nom de la base de données.  
  
> [!IMPORTANT]  
> SSMA pour Access ne prend pas en charge la connexion à la base de données master dans SQL Azure.  
  
**Nom d'utilisateur**  
  
Entrez le nom d’utilisateur SSMA utilisera pour se connecter à la base de données SQL Azure  
  
**Mot de passe**  
  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué.  
  
**Encrypt**  
  
SSMA recommande une connexion chiffrée pour SQL Azure.  
  
## <a name="create-azure-database"></a>Créer une base de données Azure  
Pour créer une nouvelle base de données azure, suivez les étapes suivantes  
  
1.  Cliquez sur le bouton Parcourir qui n’est présent dans la connexion à la boîte de dialogue de SQL Azure  
  
2.  S’il n’y a aucune base de données, deux éléments de menu s’affichent  
  
    1.  **(aucune base)**  qui est désactivé et grisé de tout le temps  
  
    2.  **Créer la nouvelle base de données** qui est toujours activée, ce qui permet de créer une nouvelle base de données azure sur le compte de SQL Azure. Lorsque vous cliquez sur cet élément de menu, Créer boîte de dialogue base de données azure est établie avec le nom de la base de données et la taille.  
  
3.  Au moment de la création de base de données, ces deux paramètres est donné comme entrée.  
  
    1.  **Nom de la base de données :** Entrez le nom de la base de données.  
  
    2.  **Taille de la base de données :** Sélectionnez la taille de la base de données dont vous avez besoin pour créer dans SQL Azure compte.  
  
