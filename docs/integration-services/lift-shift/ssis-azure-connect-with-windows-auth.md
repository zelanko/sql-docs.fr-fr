---
title: Se connecter à des sources de données et des partages de fichiers avec l’authentification Windows | Microsoft Docs
description: Découvrez comment configurer le catalogue SSIS dans Azure SQL Database et Azure-SSIS Integration Runtime pour exécuter des packages qui se connectent à des sources de données et à des partages de fichiers avec l’authentification Windows.
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: c2b7a091b4bfe5add722ad224adc175b06817a74
ms.sourcegitcommit: c582de20c96242f551846fdc5982f41ded8ae9f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37066019"
---
# <a name="connect-to-data-sources-and-file-shares-with-windows-authentication-from-ssis-packages-in-azure"></a>Se connecter à des sources de données et à des partages de fichiers avec l’authentification Windows à partir de packages SSIS sur Azure
Vous pouvez utiliser l’authentification Windows pour vous connecter à des sources de données et à des partages de fichiers dans le même réseau virtuel qu’Azure-SSIS Integration Runtime (IR), aussi bien localement/sur des machines virtuelles Azure que dans Azure Files. Il existe trois moyens de se connecter à des sources de données et à des partages de fichiers avec l’authentification Windows à partir de packages SSIS en cours d’exécution dans Azure-SSIS IR :

| Méthode de connexion | Portée effective | Étape de configuration | Méthode d’accès dans des packages | Nombre de jeux d’informations d’identification et ressources connectées | Type de ressources connectées | 
|---|---|---|---|---|---|
| Conserver les informations d’identification avec la commande `cmdkey` | Par runtime Azure-SSIS IR | Exécutez la commande `cmdkey` dans un script d’installation personnalisée (`main.cmd`) lors de l’approvisionnement/la reconfiguration de votre runtime Azure-SSIS IR, par exemple, `cmdkey /add:fileshareserver /user:xxx /pass:yyy`.<br/><br/> Pour plus d’informations, voir [Personnaliser l’installation du runtime Azure-SSIS IR](https://docs.microsoft.com/en-us/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup). | Accédez directement aux ressources dans les packages en suivant le chemin d’accès UNC, par exemple, `\\fileshareserver\folder`. | Prise en charge de plusieurs jeux d’informations d’identification pour différentes ressources connectées | - Partages de fichiers localement/sur des machines virtuelles Azure<br/><br/> - Azure Files, voir [Utiliser un partage de fichiers Azure](https://docs.microsoft.com/en-us/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - SQL Server avec authentification Windows<br/><br/> - Autres ressources avec authentification Windows |
| Configurer un contexte d’exécution au niveau du catalogue | Par runtime Azure-SSIS IR | Exécutez la procédure stockée `catalog.set_execution_credential` SSIDB pour définir un « contexte d’exécution en tant que ».<br/><br/> Pour plus d’informations, voir la suite de cet article. | Accédez directement aux ressources dans les packages. | Prise en charge d’un seul jeu d’informations d’identification pour toutes les ressources connectées | - Partages de fichiers localement/sur des machines virtuelles Azure<br/><br/> - Azure Files, voir [Utiliser un partage de fichiers Azure](https://docs.microsoft.com/en-us/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - SQL Server avec authentification Windows<br/><br/> - Autres ressources avec authentification Windows | 
| Monter des lecteurs à l’exécution du package (non-persistance) | Par package | Exécutez la commande `net use` dans la tâche Exécuter le processus ajoutée au début du flux de contrôle de vos packages, par exemple, `net use D: \\fileshareserver\sharename`. | Accédez aux partages de fichiers par le biais de lecteurs mappés. | Prise en charge de plusieurs lecteurs pour différents partages de fichiers | - Partages de fichiers localement/sur des machines virtuelles Azure<br/><br/> - Azure Files, voir [Utiliser un partage de fichiers Azure](https://docs.microsoft.com/en-us/azure/storage/files/storage-how-to-use-files-windows) |
|||||||

> [!WARNING]
> Si vous n’utilisez aucune des méthodes ci-dessus pour vous connecter à des sources de données et à des partages de fichiers avec l’authentification Windows, les packages qui dépendent de l’authentification Windows ne pourront pas s’y connecter et échoueront à l’exécution. 

La suite de cet article explique comment configurer le catalogue SSIS dans Azure SQL Database pour exécuter des packages qui utilisent l’authentification Windows afin de se connecter à des sources de données et à des partages de fichiers. 

## <a name="you-can-only-use-one-set-of-credentials"></a>Vous ne pouvez utiliser qu’un seul jeu d’informations d’identification
Avec cette méthode, vous ne pourrez utiliser qu’un seul jeu d’informations d’identification dans un package. Jusqu’à ce que vous les changiez ou les supprimiez, les informations d’identification de domaine que vous indiquez en suivant les étapes de cet article s’appliquent à toutes les exécutions de packages, interactives ou planifiées, sur votre runtime Azure-SSIS IR. Si votre package doit se connecter à plusieurs sources de données et à plusieurs partages de fichiers avec différents jeux d’informations d’identification, il peut être intéressant de se tourner vers les autres méthodes décrites ci-dessus.

## <a name="provide-domain-credentials-for-windows-authentication"></a>Fournir des informations d’identification de domaine pour l’authentification Windows
Pour indiquer des informations d’identification de domaine qui permettent aux packages d’utiliser l’authentification Windows afin de se connecter à des sources de données/partages de fichiers locaux, effectuez les actions suivantes :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB). Pour plus d’informations, consultez [Se connecter au catalogue SSIS (SSISDB) dans Azure](ssis-azure-connect-to-catalog-database.md).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante et fournissez les informations d’identification de domaine appropriées :

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  Exécutez vos packages SSIS. Les packages utilisent les informations d’identification que vous avez indiquées pour se connecter aux sources de données/partages de fichiers locaux avec l’authentification Windows.

### <a name="view-domain-credentials"></a>Afficher les informations d’identification de domaine
Pour afficher les informations d’identification de domaine actives, effectuez les actions suivantes :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante et vérifiez la sortie :

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>Effacer les informations d’identification de domaine
Pour effacer et supprimer les informations d’identification que vous avez fournies, comme indiqué dans cet article, effectuez les actions suivantes :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante :

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-an-on-premises-sql-server"></a>Se connecter à un serveur SQL Server local
Pour vérifier si vous pouvez vous connecter à une instance SQL Server locale, effectuez les actions suivantes :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez la commande suivante pour démarrer SQL Server Management Studio (SSMS) avec les informations d’identification de domaine à utiliser :

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  À partir de SSMS, vérifiez si vous pouvez vous connecter à l’instance SQL Server locale à utiliser.

### <a name="prerequisites"></a>Conditions préalables requises
Pour vous connecter à un serveur SQL Server local à partir d’un package s’exécutant sur Azure, vous devez satisfaire aux prérequis suivants :

1.  Dans le Gestionnaire de Configuration SQL Server, activez le protocole TCP/IP.
2.  Autorisez l’accès à travers le pare-feu Windows. Pour plus d’informations, consultez [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access).
3.  Pour vous connecter avec l’authentification Windows, vérifiez que votre runtime Azure-SSIS IR appartient à un réseau virtuel qui inclut également le serveur SQL Server local.  Pour plus d’informations, consultez [Joindre un runtime d’intégration Azure SSIS à un réseau virtuel](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network). Utilisez ensuite `catalog.set_execution_credential` pour fournir des informations d’identification comme décrit dans cet article.

## <a name="connect-to-an-on-premises-file-share"></a>Se connecter à un partage de fichiers local
Pour vérifier si vous pouvez vous connecter à un partage de fichiers local, effectuez les actions suivantes :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez la commande suivante. Cette commande ouvre une fenêtre d’invite de commandes avec les informations d’identification de domaine à utiliser. Elle teste ensuite la connectivité au partage de fichiers en obtenant une liste de répertoires.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Vérifiez si la liste de répertoires est retournée pour le partage de fichiers local à utiliser.

## <a name="connect-to-a-file-share-on-an-azure-vm"></a>Se connecter à un partage de fichiers sur une machine virtuelle Azure
Pour vous connecter à un partage de fichiers sur une machine virtuelle Azure, procédez comme suit :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée `catalog.set_execution_credential` comme indiqué dans les options suivantes :

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>Se connecter à un partage de fichiers dans Azure Files
Pour plus d’informations sur Azure Files, consultez [Azure Files](https://azure.microsoft.com/services/storage/files/).

Pour vous connecter à un partage de fichiers dans Azure Files, effectuez les actions suivantes :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée `catalog.set_execution_credential` comme indiqué dans les options suivantes :

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Étapes suivantes
- Déployez un package. Pour plus d’informations, consultez [Déployer un projet SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Exécutez un package. Pour plus d’informations, consultez [Exécuter un package SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Planifiez un package. Pour plus d’informations, consultez [Planifier des packages SSIS dans Azure](ssis-azure-schedule-packages.md).