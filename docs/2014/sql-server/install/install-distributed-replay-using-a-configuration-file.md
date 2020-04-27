---
title: Installer Distributed Replay à l’aide d’un fichier de configuration | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3259232c-6963-4c9c-9d10-ae42aa262eef
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9db8127a9a43478d891d5955190bd594fb6647b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094574"
---
# <a name="install-distributed-replay-using-a-configuration-file"></a>Installer Distributed Replay à l'aide d'un fichier de configuration
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet de générer un fichier de configuration basé sur les entrées utilisateur et les entrées système par défaut. Si vous spécifiez que vous souhaitez que les outils d'administration soient installés, vous pouvez utiliser le fichier de configuration pour déployer les trois composants Distributed Replay (outil d'administration, Distributed Replay Controller et Distributed Replay Client). Il prend en charge l'installation, la réparation et la désinstallation des composants Distributed Replay.  
  
 Le programme d'installation ne prend en charge l'utilisation du fichier de configuration qu'à l'aide de la ligne de commande. L'ordre de traitement des paramètres lors de l'utilisation du fichier de configuration est décrit ci-dessous :  
  
-   Le fichier de configuration remplace les valeurs par défaut d'un package.  
  
-   Les valeurs de la ligne de commande remplacent les valeurs du fichier de configuration.  
  
 Pour plus d’informations sur l’utilisation d’un fichier de configuration, consultez [installer SQL Server 2014 à l’aide d’un fichier de configuration](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).  
  
> [!IMPORTANT]  
>  Une fois que vous avez installé Distributed Replay, vous devez créer des règles de pare-feu sur le contrôleur et les ordinateurs clients, et accorder des autorisations à chaque ordinateur client sur le serveur cible. Pour plus d’informations, consultez [Suivre les étapes consécutives à l’installation](../../tools/distributed-replay/complete-the-post-installation-steps.md).  
  
### <a name="to-generate-a-configuration-file"></a>Pour générer un fichier de configuration  
  
1.  Suivez le déroulement des étapes de l'Assistant Installation jusqu'à la page **Prêt pour l'installation** . Le chemin d'accès au fichier de configuration est spécifié dans la page **Prêt pour l'installation** , dans la section relative au chemin d'accès du fichier de configuration.  
  
2.  Annulez l'exécution du programme d'installation sans réellement terminer l'installation afin de générer le fichier INI.  
  
### <a name="to-install-distributed-replay-using-the-configuration-file"></a>Pour installer Distributed Replay à l'aide du fichier de configuration  
  
-   Exécutez l'installation à partir de l'invite de commandes et spécifiez le fichier ConfigurationFile.ini à l'aide du paramètre ConfigurationFile.  
  
 **Exemple de syntaxe**  
  
 Voici un exemple montrant comment spécifier le fichier de configuration lors de l'invite de commandes :  
  
```  
Setup.exe /CTLRSVCPASSWORD="ctlrsvcpswd" /CLTSVCPASSWORD="cltsvcpswd" / ConfigurationFile=ConfigurationFile.INI\  
```  
  
> [!NOTE]  
>  Vous devez spécifier les deux mots de passe dans la ligne de commande car il n'est pas possible de les configurer dans le fichier de configuration.  
  
  
