---
title: Mettre à niveau le schéma des bases de données DQS après avoir installé la mise à jour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e4d4f5af2a9b0c58e8cef89f143e4ec42cb03695
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53372921"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a>Mettre à niveau le schéma des bases de données DQS après avoir installé la mise à jour SQL Server
  Après avoir installé une mise à jour SQL Server (correctif, correctif logiciel ou mise à jour cumulative) sur une instance DQS configurée précédemment, vous pouvez être amené à mettre à niveau le schéma des bases de données DQS en exécutant le fichier DQSInstaller.exe avec le paramètre de ligne de commande **upgrade** . Sinon, l'erreur suivante peut s'afficher lors de la tentative de connexion au serveur de qualité des données à l'aide de votre client de qualité des données :  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 La mise à niveau du schéma des bases de données DQS n'a aucun effet sur les données existantes dans les bases de données DQS (bases de connaissances, projets de qualité des données et résultats exportés dans la base de données DQS_STAGING_DATA). Cependant, vous devez sauvegarder vos bases de données DQS avant de mettre à niveau le schéma des bases de données DQS afin d'empêcher toute perte accidentelle de données lors de la mise à niveau du schéma. Pour plus d'informations sur la sauvegarde des bases de données DQS, consultez [Sauvegarde et restauration de bases de données DQS](../backing-up-and-restoring-dqs-databases.md).  
  
> [!NOTE]  
>  La majorité des mises à jour SQL Server nécessite une mise à niveau du schéma des bases de données DQS. Pour plus d’informations sur les mises à jour de SQL Server qui nécessitent une mise à niveau du schéma de bases de données DQS, consultez le graphique à l’étape 1.A [mettre à niveau DQS : Installation des mises à jour cumulatives ou correctifs logiciels sur Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Vous devez être connecté en tant que membre du groupe Administrateurs sur l'ordinateur [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe sysadmin dans l'instance de SQL Server où le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] est installé.  
  
### <a name="to-upgrade-dqs-databases-schema"></a>Pour mettre à niveau le schéma des bases de données DQS  
  
1.  (Recommandé) Sauvegardez vos bases de données DQS avant de mettre à niveau le schéma. Pour plus d'informations sur la sauvegarde des bases de données DQS, consultez [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).  
  
2.  Démarrez l'invite de commandes.  
  
3.  À l'invite de commandes, remplacez votre répertoire à l'emplacement où DQSInstaller.exe est disponible. Si vous avez installé l'instance par défaut de SQL Server, le fichier DQSInstaller.exe sera copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn :  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  À l'invite de commandes, tapez la commande suivante et appuyez sur Entrée :  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  Le programme d'installation vous invite à sauvegarder les bases de données DQS avant de continuer. Si vous avez déjà sauvegardé vos bases de données DQS, tapez `Y` ou `Yes`, puis appuyez sur Entrée pour poursuivre la mise à niveau.  
  
6.  Un message d'achèvement s'affiche une fois la mise à niveau du schéma des bases de données DQS terminée.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Connectez-vous au serveur de qualité des données à partir d'une application client de qualité des données.  
  
 Pour plus d’informations sur la mise à niveau DQS schéma des bases de données après l’installation de SQL Server met à jour et procédures de dépannage associées, consultez [mettre à niveau DQS : Installation des mises à jour cumulatives ou correctifs logiciels sur Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Data Quality Services](install-data-quality-services.md)   
 [Mettre à niveau des assemblys SQLCLR après une mise à jour de .NET Framework](upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
