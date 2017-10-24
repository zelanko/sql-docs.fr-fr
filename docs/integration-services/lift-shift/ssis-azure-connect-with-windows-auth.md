---
title: "Se connecter aux sources de données locale avec l’authentification Windows | Documents Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 1e3d9736612211038991489a4bd858d1ff89d333
ms.openlocfilehash: 1b60d877c6c75a77dd16fa8cb1704e10baf36bdb
ms.contentlocale: fr-fr
ms.lasthandoff: 10/19/2017

---
# <a name="connect-to-on-premises-data-sources-with-windows-authentication"></a>Se connecter aux sources de données locale avec l’authentification Windows
Cet article décrit comment configurer le catalogue SSIS sur une base de données SQL Azure pour exécuter des packages qui utilisent l’authentification Windows pour se connecter aux sources de données sur site.

Les informations d’identification de domaine que vous fournissez lorsque vous suivez les étapes décrites dans cet article s’appliquent à toutes les exécutions de package sur l’instance de base de données SQL jusqu'à ce que vous modifiez ou supprimez les informations d’identification.

## <a name="prerequisite"></a>Condition préalable
Avant de configurer les informations d’identification de domaine pour l’authentification Windows, vérifiez si un ordinateur non joint à un domaine peut se connecter à votre source de données locale dans `runas` mode.

### <a name="connecting-to-sql-server"></a>Connexion à SQL Server
Pour vérifier si vous pouvez vous connecter à un ordinateur local SQL Server, procédez comme suit :

1.  Pour exécuter ce test, rechercher un ordinateur non joint au domaine.

2.  Sur l’ordinateur non joint au domaine, exécutez la commande suivante pour démarrer SQL Server Management Studio (SSMS) avec les informations d’identification de domaine que vous souhaitez utiliser :

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  À partir de SSMS, vérifiez si vous pouvez vous connecter au serveur SQL local que vous souhaitez utiliser.

### <a name="connecting-to-a-file-share"></a>Connexion à un partage de fichiers
Pour vérifier si vous pouvez vous connecter à un partage de fichiers local, procédez comme suit :

1.  Pour exécuter ce test, rechercher un ordinateur non joint au domaine.

2.  Sur l’ordinateur non joint au domaine, exécutez la commande suivante. Cette commande ouvre une prommpt de commande avec les informations d’identification de domaine que vous souhaitez utiliser, puis teste la connectivité au partage de fichiers en obtenant une liste de répertoires.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Vérifiez si la liste des répertoires est retournée pour localement le fichier de partage que vous souhaitez utiliser.

## <a name="provide-domain-credentials"></a>Fournir des informations d’identification de domaine
Pour fournir des informations d’identification de domaine qui vous permettent de packages d’utiliser l’authentification Windows pour se connecter aux sources de données locale, procédez comme suit :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à la base de données SQL qui héberge la base de données du catalogue SSIS (SSISDB). Pour plus d’informations, consultez [se connecter à la base de données de catalogue SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

2.  Avec SSISDB en tant que base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante et fournir des informations d’identification de domaine approprié :

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```
4.  Exécuter vos packages SSIS. Les packages utilisent les informations d’identification que vous avez fourni pour vous connecter aux sources de données locale avec l’authentification Windows.

## <a name="view-domain-credentials"></a>Informations d’identification de domaine de vue
Pour afficher les informations d’identification de domaine actif, procédez comme suit :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à la base de données SQL qui héberge la base de données du catalogue SSIS (SSISDB).

2.  Avec SSISDB en tant que base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante et vérifiez la sortie :

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

## <a name="clear-domain-credentials"></a>Informations d’identification de domaine clair
Pour effacer et supprimer les informations d’identification que vous avez fourni comme décrit dans cet article, procédez comme suit :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à la base de données SQL qui héberge la base de données du catalogue SSIS (SSISDB).

2.  Avec SSISDB en tant que base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante :

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-file-shares"></a>Se connecter aux partages de fichiers
Vous pouvez utiliser l’authentification Windows pour se connecter aux partages de fichiers dans le même réseau virtuel en tant que le Runtime d’intégration Azure SSIS à la fois localement et sur les machines virtuelles.

Pour vous connecter à un partage de fichiers sur une machine virtuelle Azure, procédez comme suit :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à la base de données SQL qui héberge la base de données du catalogue SSIS (SSISDB).

2.  Avec SSISDB en tant que base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée suivante :

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="next-steps"></a>Étapes suivantes
- Déployer un package. Pour plus d’informations, consultez [déployer un projet SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Exécuter un package. Pour plus d’informations, consultez [exécuter un package SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Planifier un package. Pour plus d’informations, consultez [du package SSIS de la planification d’exécution sur Azure](ssis-azure-schedule-packages.md)

