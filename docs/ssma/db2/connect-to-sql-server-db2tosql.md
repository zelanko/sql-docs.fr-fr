---
title: Se connecter à SQL Server (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: bc14a072-8949-4ee0-a4b4-ada55fe8df5c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0bc3c92067d1fd8240cc17db03de7dac409a0123
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52414406"
---
# <a name="connect-to-sql-server-db2tosql"></a>Se connecter à SQL Server (DB2ToSQL)
Utilisez le **se connecter à SQL Server** boîte de dialogue se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous souhaitez migrer vers. Pour accéder à la **se connecter à SQL Server** boîte de dialogue le **fichier** menu, cliquez sur **se connecter à SQL Server**.  
  
## <a name="options"></a>Options  
**Nom du serveur**  
Entrez ou sélectionnez l’instance de SQL Server pour se connecter à. Par défaut, l’instance connectée à la plus récemment s’affiche.  
  
-   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer soit **localhost** ou un point (**.**).  
  
-   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
-   Si vous vous connectez à une instance nommée sur un autre ordinateur, permet d’entrer le nom d’ordinateur, une barre oblique inverse et le nom d’instance, tel que *MyServer*\\*MyInstance*.  
  
**Port du serveur**  
Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas configuré pour accepter les connexions sur la valeur par défaut le port (1433), entrez le numéro de port. Sinon, laissez cette valeur vide.  
  
**Sauvegarde de la base de données**  
Spécifiez la base de données pour migrer des objets et données. Cette option n’est pas disponible lors de la reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Authentification**  
Sélectionnez la méthode d’authentification qui est utilisée pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour utiliser votre compte Windows actuel, sélectionnez l’authentification Windows. Pour spécifier un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion et mot de passe, sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.  
  
**Nom d'utilisateur**  
Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, entrez le nom de connexion pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous utilisez l’authentification Windows, cette option n’est pas disponible.  
  
**Mot de passe**  
Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, entrez le mot de passe de connexion sur cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous utilisez l’authentification Windows, cette option n’est pas disponible.  
  
**Chiffrer la connexion**  
Si vous souhaitez vous connecter en toute sécurité pour SQL Server, veillez à utiliser de chiffrer la connexion en vérifiant la **chiffrer la connexion** case à cocher.  
  
**Faire confiance au certificat de serveur**  
Si vous souhaitez utiliser cette option, sélectionnez le **faire confiance au certificat serveur** case à cocher.  
  
> [!NOTE]  
> Pour activer **faire confiance au certificat serveur**, « Chiffrer » doit être définie sur **True**.  
  
