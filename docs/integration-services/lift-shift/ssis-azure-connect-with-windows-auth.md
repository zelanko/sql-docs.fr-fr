---
title: "Se connecter à des sources de données locales et des partages de fichiers Azure avec l’authentification Windows | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9235ffd3225e76ee94067519c72e997c451d9893
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authentication"></a>Se connecter à des sources de données locales et des partages de fichiers Azure avec l’authentification Windows
Cet article explique comment configurer le catalogue SSIS sur Azure SQL Database pour exécuter des packages qui utilisent l’authentification Windows afin de se connecter à des sources de données locales et des partages de fichiers Azure.

Les informations d’identification de domaine que vous fournissez quand vous suivez les étapes de cet article s’appliquent à toutes les exécutions de package sur l’instance SQL Database jusqu’à ce que vous changiez ou supprimiez les informations d’identification.

## <a name="connect-to-on-premises-data-sources"></a>Se connecter à des sources de données locales

### <a name="prerequisite"></a>Condition préalable
Avant de configurer les informations d’identification de domaine pour l’authentification Windows, vérifiez si un ordinateur non membre d’un domaine peut se connecter à votre source de données locale en mode `runas`.

#### <a name="connecting-to-sql-server"></a>Connexion à SQL Server
Pour vérifier si vous pouvez vous connecter à une instance SQL Server locale, effectuez les actions suivantes :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez la commande suivante pour démarrer SQL Server Management Studio (SSMS) avec les informations d’identification de domaine à utiliser :

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  À partir de SSMS, vérifiez si vous pouvez vous connecter à l’instance SQL Server locale à utiliser.

#### <a name="connecting-to-a-file-share"></a>Connexion à un partage de fichiers
Pour vérifier si vous pouvez vous connecter à un partage de fichiers local, effectuez les actions suivantes :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez la commande suivante. Cette commande ouvre une fenêtre d’invite de commandes avec les informations d’identification de domaine à utiliser. Elle teste ensuite la connectivité au partage de fichiers en obtenant une liste de répertoires.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Vérifiez si la liste de répertoires est retournée pour le partage de fichiers local à utiliser.

### <a name="provide-domain-credentials"></a>Fournir des informations d’identification de domaine
Pour fournir des informations d’identification de domaine qui permettent aux packages d’utiliser l’authentification Windows afin de se connecter à des sources de données locales, effectuez les actions suivantes :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB). Pour plus d’informations, consultez [Se connecter à la base de données de catalogues SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante et fournissez les informations d’identification de domaine appropriées :

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```
4.  Exécutez vos packages SSIS. Les packages utilisent les informations d’identification que vous avez fournies pour se connecter aux sources de données locales via l’authentification Windows.

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

## <a name="connect-to-file-shares"></a>Se connecter aux partages de fichiers
Vous pouvez utiliser l’authentification Windows pour vous connecter aux partages de fichiers situés dans le même réseau virtuel que le runtime d’intégration Azure SSIS, aussi bien localement que sur des machines virtuelles Azure et dans Azure Files. Pour plus d’informations sur Azure Files, consultez [Azure Files](https://azure.microsoft.com/services/storage/files/).

Pour vous connecter à un partage de fichiers sur une machine virtuelle Azure ou un partage de fichiers Azure, effectuez les actions suivantes :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée `catalog.set_execution_credential` comme indiqué dans les options suivantes :

    a.  Pour vous connecter à un partage de fichiers sur une machine virtuelle Azure, exécutez la procédure stockée suivante :

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

    b.  Pour vous connecter à un partage de fichiers Azure (en d’autres termes, à Azure Files), exécutez la procédure stockée suivante :

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Étapes suivantes
- Déployez un package. Pour plus d’informations, consultez [Déployer un projet SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Exécutez un package. Pour plus d’informations, consultez [Exécuter un package SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Planifiez un package. Pour plus d’informations, consultez [Planifier l’exécution d’un package SSIS sur Azure](ssis-azure-schedule-packages.md).
