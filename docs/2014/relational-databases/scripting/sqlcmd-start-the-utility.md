---
title: Démarrer l’utilitaire sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec1ec91705dfb9194f42c079cb7b3d5100c9d396
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090107"
---
# <a name="start-the-sqlcmd-utility"></a>Démarrer l'utilitaire sqlcmd
  Pour vous servir de l'utilitaire `sqlcmd`, vous devez le lancer, puis vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez vous connecter à une instance par défaut ou nommée. La première étape consiste à démarrer l'utilitaire `sqlcmd`.  
  
> [!NOTE]  
>  L'authentification Windows est le mode d'authentification par défaut pour `sqlcmd`. Pour utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez spécifier un nom d’utilisateur et un mot de passe en utilisant les options **-U** et **-P** .  
  
> [!NOTE]  
>  Par défaut, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] s’installe en tant qu’instance nommée **sqlexpress**.  
  
 Si vous ne vous êtes pas connecté préalablement à cette instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], vous devez configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accepter les connexions.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>Pour démarrer l'utilitaire sqlcmd et établir une connexion à une instance par défaut de SQL Server  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**. Dans la zone **Ouvrir** , tapez **cmd**, puis cliquez sur **OK** pour ouvrir une fenêtre d'invite de commandes.  
  
2.  À l’invite de commandes, tapez `sqlcmd`.  
  
3.  Appuyez sur Entrée.  
  
     Vous bénéficiez maintenant d'une connexion approuvée à l'instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est exécutée sur votre ordinateur.  
  
     **1 >** est le `sqlcmd` invite qui spécifie le numéro de ligne. Chaque fois que vous appuyez sur ENTRÉE, le numéro augmente de un.  
  
4.  Pour mettre fin à la `sqlcmd` session, tapez `EXIT` à la `sqlcmd` invite.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>Pour démarrer l'utilitaire sqlcmd et établir une connexion à une instance nommée de SQL Server  
  
1.  Ouvrez une invite de commandes fenêtre, puis tapez `sqlcmd -S` *Monserveur\nom_instance*. Remplacez *mon_serveur\nom_instance[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le nom de l’ordinateur et de l’instance de* à laquelle vous souhaitez vous connecter.  
  
2.  Appuyez sur Entrée.  
  
     Le `sqlcmd` invite (1 >) indique que vous êtes connecté à l’instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] entrées sont stockées dans une mémoire tampon. Elles sont exécutées en tant que lot lorsque la commande GO est rencontrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter des fichiers de script Transact-SQL à l'aide de sqlcmd](sqlcmd-run-transact-sql-script-files.md)  
  
  
