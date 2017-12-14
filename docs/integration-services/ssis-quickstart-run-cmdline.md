---
title: "Exécuter un package SSIS à partir de l’invite de commandes | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c2b83605714e01961c50d71e83ba57691bc3833
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Exécuter un package SSIS à partir de l’invite de commandes avec DTExec.exe
Ce didacticiel de démarrage rapide montre comment exécuter un package SSIS à partir de l’invite de commandes en exécutant `DTExec.exe` avec les paramètres appropriés.

> [!NOTE]
> La méthode décrite dans cet article n’a pas été testée avec des packages déployés sur un serveur Azure SQL Database.

Pour plus d’informations sur `DTExec.exe`, consultez [Utilitaire dtexec](https://docs.microsoft.com/en-us/sql/integration-services/packages/dtexec-utility).

## <a name="run-a-package-with-dtexec"></a>Exécuter un package avec dtexec

Si le dossier qui contient `DTExec.exe` ne figure pas dans votre variable d’environnement `path`, vous devrez peut-être utiliser la commande `cd` pour basculer vers son répertoire. Pour SQL Server 2017, ce dossier est généralement `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

Avec les valeurs de paramètres utilisées dans l’exemple suivant, le programme exécute le package qui se trouve au chemin de dossier spécifié sur le serveur SSIS, autrement dit le serveur qui héberge la base de données du catalogue SSIS (SSISDB). Le paramètre `/Server` fournit le nom du serveur. Le programme se connecte en tant que l’utilisateur actuel avec l’Authentification intégrée de Windows. Pour utiliser l’authentification SQL, spécifiez les paramètres `/User` et `Password` avec les valeurs appropriées.

1. Ouvrez une fenêtre d'invite de commandes.

2. Exécutez `DTExec.exe` et fournissez des valeurs pour au moins les paramètres `ISServer` et `Server`, comme indiqué dans l’exemple suivant :

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour exécuter un package.
    - [Exécuter un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécuter un package SSIS avec C#](./ssis-quickstart-run-dotnet.md) 
