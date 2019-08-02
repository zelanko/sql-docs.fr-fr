---
title: Le démarrage rapide pour la vérification de R existe dans SQL Server
description: Démarrage rapide pour vérifier que R et Machine Learning Services existent dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 072a6f34a7cb91505d77356d6ec3835915c310d0
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715403"
---
# <a name="quickstart-verify-r-exists-in-sql-server"></a>Démarrage rapide : Vérifier que R existe dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server prend en charge le langage R pour l’analyse de la science des données sur les données résidentes SQL Server. Votre script R peut être constitué de fonctions R Open source, de bibliothèques R tierces ou de bibliothèques Microsoft R intégrées, telles que [RevoScaleR](../r/revoscaler-overview.md) pour l’analyse prédictive à grande échelle.

L’exécution du script s’effectue via des procédures stockées, à l’aide de l’une des approches suivantes:

+ Procédure stockée [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) intégrée, transmettant le script R dans en tant que paramètre d’entrée.
+ Renvoyez le script R dans une [procédure stockée personnalisée](sqldev-in-database-r-for-sql-developers.md) que vous créez.

Dans ce guide de démarrage rapide, vous allez vérifier que [SQL Server machine learning services](../what-is-sql-server-machine-learning.md) ou [SQL Server 2016 R services](../r/sql-server-r-services.md) est installé et configuré.

## <a name="prerequisites"></a>Prérequis

Cet exercice requiert l’accès à une instance de SQL Server avec l’un des éléments suivants déjà installés:

+ [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md)avec le langage R installé
+ [SQL Server 2016 R services](../install/sql-r-services-windows-install.md)

Votre instance de SQL Server peut se trouver dans une machine virtuelle Azure ou en local. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que **SQL Server Launchpad service** est en cours d’exécution avant de commencer.

Vous avez également besoin d’un outil pour exécuter des requêtes SQL. Vous pouvez exécuter les scripts R à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-r-exists"></a>Vérifier l’existence de R

Vous pouvez vérifier que Machine Learning Services (avec R) est activé pour votre instance SQL Server et quelle version de R est installée. Suivez les étapes ci-dessous.

1. Ouvrez SQL Server Management Studio et connectez-vous à votre instance SQL Server.

2. Exécutez le code ci-dessous. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'R',
    @script=N'print(version)';
    GO
    ```

3. La fonction `print` R retourne la version dans la fenêtre **messages** . Dans l’exemple de sortie ci-dessous, vous pouvez voir que SQL Server dans ce cas, R version 3.3.3 est installé.

    **Résultats**

    ```text
    platform       x86_64-w64-mingw32          
    arch           x86_64                      
    os             mingw32                     
    system         x86_64, mingw32             
    status                                     
    major          3                           
    minor          3.3                         
    year           2017                        
    month          03                          
    day            06                          
    svn rev        72310                       
    language       R                           
    version.string R version 3.3.3 (2017-03-06)
    nickname       Another Canoe               
    ```

Si vous recevez des erreurs à partir de cette requête, éliminez les problèmes d’installation. La configuration après installation est requise pour permettre l’utilisation de bibliothèques de code externes. Consultez [installer SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) ou [installer SQL Server 2016 R services](../install/sql-r-services-windows-install.md). De même, assurez-vous que le service Launchpad est en cours d’exécution.

Selon votre environnement, vous pouvez être amené à activer les comptes de travail R pour vous connecter à SQL Server, installer des bibliothèques réseau supplémentaires, activer l’exécution de code à distance ou redémarrer l’instance une fois que tout est configuré. Pour plus d’informations, consultez [FAQ sur l’installation et la mise à niveau de R services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="list-r-packages"></a>Répertorier les packages R

Microsoft fournit un certain nombre de packages R préinstallés avec Machine Learning Services dans votre instance SQL Server. Pour afficher la liste des packages R installés, y compris les informations sur la version, les dépendances, la licence et le chemin d’accès de la bibliothèque, suivez les étapes ci-dessous.

1. Exécutez le script ci-dessous sur votre instance SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
    OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
    WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
        , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
    ```

2. La sortie provient `installed.packages()` de dans R et est retournée en tant que jeu de résultats.

    **Résultats**

    ![Packages installés dans R](./media/rsql-installed-packages.png)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez confirmé que votre instance est prête à fonctionner avec R, examinez de plus près une interaction R de base.

> [!div class="nextstepaction"]
> [Démarrage rapide : Script R «Hello World» dans SQL Server](quickstart-r-run-using-tsql.md)
