---
title: Mettre à niveau le schéma des bases de données DQS après l’installation de SQL Server Update
description: Apprenez à mettre à niveau l’instance de Data Quality Services (DQS) à l’aide de DQSInstaller.exe une fois que SQL Server a été mis à jour par un correctif, un correctif ou une mise à jour cumulative.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: swinarko
ms.author: sawinark
ms.openlocfilehash: e2491a46bb4c0e07c61b5c827a7b8f666d09d94c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897798"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a>Mettre à niveau le schéma des bases de données DQS après l’installation de SQL Server Update

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Après avoir installé une mise à jour SQL Server (correctif, correctif logiciel ou mise à jour cumulative) sur une instance DQS configurée précédemment, vous pouvez être amené à mettre à niveau le schéma des bases de données DQS en exécutant le fichier DQSInstaller.exe avec le paramètre de ligne de commande **upgrade** . Sinon, l'erreur suivante peut s'afficher lors de la tentative de connexion au serveur de qualité des données à l'aide de votre client de qualité des données :  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 La mise à niveau du schéma des bases de données DQS n'a aucun effet sur les données existantes dans les bases de données DQS (bases de connaissances, projets de qualité des données et résultats exportés dans la base de données DQS_STAGING_DATA). Cependant, vous devez sauvegarder vos bases de données DQS avant de mettre à niveau le schéma des bases de données DQS afin d'empêcher toute perte accidentelle de données lors de la mise à niveau du schéma. Pour plus d'informations sur la sauvegarde des bases de données DQS, consultez [Sauvegarde et restauration de bases de données DQS](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
> [!NOTE]  
>  La majorité des mises à jour SQL Server nécessite une mise à niveau du schéma des bases de données DQS. Pour plus d’informations sur les mises à jour SQL Server qui nécessitent une mise à niveau du schéma des bases de données DQS, consultez le graphique à l’étape 1.A dans [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Mise à niveau de DQS : installation de mises à jour cumulatives ou de correctifs logiciels sur Data Quality Services.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Vous devez être connecté en tant que membre du groupe Administrateurs sur l'ordinateur [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe sysadmin dans l'instance de SQL Server où le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] est installé.  
  
### <a name="to-upgrade-dqs-databases-schema"></a>Pour mettre à niveau le schéma des bases de données DQS  
  
1.  (Recommandé) Sauvegardez vos bases de données DQS avant de mettre à niveau le schéma. Pour plus d'informations sur la sauvegarde des bases de données DQS, consultez [Sauvegarde et restauration de bases de données DQS](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
2.  Démarrez l'invite de commandes.  
  
3.  À l'invite de commandes, remplacez votre répertoire à l'emplacement où DQSInstaller.exe est disponible. Si vous avez installé l’instance par défaut de SQL Server, le fichier DQSInstaller.exe est disponible dans C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  À l'invite de commandes, tapez la commande suivante et appuyez sur Entrée :  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  Le programme d'installation vous invite à sauvegarder les bases de données DQS avant de continuer. Si vous avez déjà sauvegardé vos bases de données DQS, tapez **Y** ou **Yes** et appuyez sur Entrée pour poursuivre la mise à niveau.  
  
6.  Un message d'achèvement s'affiche une fois la mise à niveau du schéma des bases de données DQS terminée.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Connectez-vous au serveur de qualité des données à partir d'une application client de qualité des données.  
  
 Pour plus d’informations sur la mise à niveau du schéma des bases de données DQS après l’installation des mises à jour SQL Server et les procédures de dépannage associées, consultez [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)(Mise à niveau de DQS : installation de mises à jour cumulatives ou de correctifs logiciels sur Data Quality Services).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Mettre à niveau des assemblys SQLCLR après une mise à jour de .NET Framework](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
