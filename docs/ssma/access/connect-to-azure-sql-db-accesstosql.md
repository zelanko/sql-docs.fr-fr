---
title: Se connecter à la base de données SQL Azure (AccessToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 511c652a221ffb3fe4392dd8f4c365de129efe13
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Connect To Azure SQL DB (AccessToSQL)
Utilisez la connexion à la boîte de dialogue SQL Azure pour se connecter à la base de données SQL Azure que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à SQL Azure**. Si vous êtes déjà connecté, la commande est **se reconnecter à SQL Azure.**  
  
## <a name="options"></a>Options  
**Nom de serveur**  
  
Sélectionnez ou entrez le nom du serveur pour se connecter à SQL Azure.  
  
**Base de données**  
  
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
  
1.  Cliquez sur le bouton Parcourir qui est présent dans la connexion à la boîte de dialogue SQL Azure  
  
2.  S’il n’y a aucune base de données, deux éléments de menu s’affichent  
  
    1.  **(bases de données introuvables)**  qui est désactivé et grisé tout le temps  
  
    2.  **Créer la nouvelle base de données** qui est toujours activé, ce qui permet de créer une nouvelle base de données azure sur le compte SQL Azure. Lorsque vous cliquez sur cet élément de menu, Créer boîte de dialogue de la base de données azure est présente et nom de la base de données et la taille.  
  
3.  Au moment de la création de la base de données, ces deux paramètres est donné comme entrée.  
  
    1.  **Nom de la base de données :** Entrez le nom de la base de données.  
  
    2.  **Taille de la base de données :** sélectionner la taille de la base de données dont vous avez besoin pour créer de compte SQL Azure.  
  
