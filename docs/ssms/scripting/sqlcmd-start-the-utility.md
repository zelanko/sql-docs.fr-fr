---
title: Démarrer l'utilitaire sqlcmd
description: Découvrez comment démarrer l’utilitaire sqlcmd, qui vous permet d’entrer des instructions Transact-SQL, des procédures système et des fichiers de script en mode SQLCMD ou dans des scripts et des travaux.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cbbf6064708f272eda5d646043ee7d43e766d104
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248098"
---
# <a name="sqlcmd---start-the-utility"></a>sqlcmd : démarrer l’utilitaire
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  [L’utilitaire sqlcmd](../../tools/sqlcmd-utility.md) vous permet d’entrer des procédures système, des fichiers de script et des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’invite de commandes dans l’Éditeur de requête en mode SQLCMD, dans un fichier de script Windows ou dans une étape de travail de système d’exploitation (Cmd.exe) d’un travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.
> [!NOTE]  
>  L’authentification Windows est le mode d’authentification par défaut pour **sqlcmd**. Pour utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez spécifier un nom d’utilisateur et un mot de passe en utilisant les options **-U** et **-P** .  
  
> [!NOTE]  
>  Par défaut, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] s’installe en tant qu’instance nommée **sqlexpress**.  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>Démarrer l’utilitaire sqlcmd et établir une connexion à une instance par défaut de SQL Server  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**. Dans la zone **Ouvrir** , tapez **cmd**, puis cliquez sur **OK** pour ouvrir une fenêtre d'invite de commandes. (Si vous ne vous êtes encore jamais connecté à cette instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , vous devrez peut-être configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour qu’il accepte les connexions.)  
  
2.  À l’invite de commandes, saisissez **sqlcmd**.  
  
3.  Appuyez sur Entrée.  
  
     Vous bénéficiez maintenant d'une connexion approuvée à l'instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est exécutée sur votre ordinateur.  
  
     **1>** correspond à l’invite **sqlcmd** indiquant le numéro de ligne. Chaque fois que vous appuyez sur ENTRÉE, le numéro augmente de un.  
  
4.  Pour terminer la session **sqlcmd** , saisissez **EXIT** sur l’invite **sqlcmd** .  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>Démarrer l’utilitaire sqlcmd et établir une connexion à une instance nommée de SQL Server  
  
1.  Ouvrez une fenêtre d’invite de commandes, puis tapez **sqlcmd -S**_mon_serveur\nom_instance_. Remplacez *mon_serveur\nom_instance[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le nom de l’ordinateur et de l’instance de* à laquelle vous souhaitez vous connecter.  
  
2.  Appuyez sur Entrée.  
  
     L’invite **sqlcmd** (1>) indique que vous êtes connecté à l’instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] entrées sont stockées dans une mémoire tampon. Elles sont exécutées en tant que lot lorsque la commande GO est rencontrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécuter des fichiers de script Transact-SQL à l'aide de sqlcmd](../../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md)  
  
  
