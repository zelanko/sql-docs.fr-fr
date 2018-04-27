---
title: Se connecter à SQL Server (MySQLToSQL) | Documents Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
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
ms.assetid: d73abd3a-80df-4293-b973-1723069db049
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1703fd9f4aa42e9c81a89d51da78e1d606aec06e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-sql-server-mysqltosql"></a>Se connecter à SQL Server (MySQLToSQL)
Utilisez le **se connecter à SQL Server** boîte de dialogue se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] que vous souhaitez migrer vers. Pour accéder à la **se connecter à SQL Server** boîte de dialogue le **fichier** menu, cliquez sur **se connecter à SQL Server**.  
  
## <a name="options"></a>Options  
**Nom du serveur**  
Entrez ou sélectionnez l’instance de SQL Server pour se connecter à. Par défaut, l’instance connectée à la plus récemment s’affiche.  
  
-   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer soit **localhost** ou un point (**.**).  
  
-   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
-   Si vous vous connectez à une instance nommée sur un autre ordinateur, permet d’entrer le nom d’ordinateur, une barre oblique inverse et le nom d’instance, tel que *MyServer*\\*MyInstance*.  
  
**Port du serveur**  
Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] n’est pas configuré pour accepter les connexions sur la valeur par défaut du port (1433), entrez le numéro de port. Sinon, laissez cette valeur vide.  
  
**Base de données**  
Spécifiez la base de données pour migrer des objets et des données. Cette option n’est pas disponible lors de la reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Authentification**  
Sélectionnez la méthode d’authentification qui est utilisée pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Pour utiliser votre compte Windows actuel, sélectionnez l’authentification Windows. Pour spécifier un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] connexion et le mot de passe, sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l’authentification.  
  
**Nom d'utilisateur**  
Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l’authentification, entrez le nom de connexion pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Si vous utilisez l’authentification Windows, cette option n’est pas disponible.  
  
**Mot de passe**  
Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l’authentification, entrez le mot de passe pour la connexion sur cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Si vous utilisez l’authentification Windows, cette option n’est pas disponible.  
  
**Chiffrer la connexion**  
Si vous souhaitez vous connecter en toute sécurité à SQL Server, veillez à utiliser de chiffrer la connexion en vérifiant la **chiffrer la connexion** case à cocher.  
  
**Faire confiance au certificat de serveur**  
Si vous souhaitez utiliser cette option, sélectionnez le **faire confiance au certificat serveur** case à cocher.  
  
> [!NOTE]  
> Pour activer **faire confiance au certificat serveur**, « Encrypt » doit être définie sur **True**.  
  
