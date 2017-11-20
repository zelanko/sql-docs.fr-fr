---
title: "Exécutez un package SSIS à partir de l’invite de commandes | Documents Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: a33b8518ec3284f5de73d38c87209057dc1c7487
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Exécutez un package SSIS à partir de l’invite de commandes avec DTExec.exe
Ce didacticiel de démarrage rapide montre comment exécuter un package SSIS à partir de l’invite de commandes en exécutant `DTExec.exe` avec les paramètres appropriés.

> [!NOTE]
> La méthode décrite dans cet article n’a pas été testée avec les packages déployés sur un serveur de base de données SQL Azure.

Pour plus d’informations sur `DTExec.exe`, consultez [utilitaire dtexec](https://docs.microsoft.com/en-us/sql/integration-services/packages/dtexec-utility).

## <a name="run-a-package-with-dtexec"></a>Exécuter un package avec dtexec

Si le dossier qui contient `DTExec.exe` ne figure pas dans votre `path` variable d’environnement, vous devrez peut-être utiliser le `cd` commande à passer à son répertoire. Pour SQL Server 2017, ce dossier est généralement `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

Avec les valeurs de paramètre utilisées dans l’exemple suivant, le programme s’exécute le package dans le chemin d’accès de dossier spécifié sur le serveur SSIS - autrement dit, le serveur qui héberge la base de données du catalogue SSIS (SSISDB). Le `/Server` paramètre fournit le nom du serveur. Le programme se connecte en tant que l’utilisateur actuel avec l’authentification intégrée de Windows. Pour utiliser l’authentification SQL, spécifiez la `/User` et `Password` paramètres avec les valeurs appropriées.

1. Ouvrez une fenêtre d'invite de commandes.

2. Exécutez `DTExec.exe` et fournir des valeurs pour au moins le `ISServer` et `Server` paramètres, comme indiqué dans l’exemple suivant :

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour exécuter un package.
    - [Exécutez un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 

