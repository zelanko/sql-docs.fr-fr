---
title: Guide de démarrage rapide pour la vérification de R existe dans SQL Server
description: Guide de démarrage rapide pour vérifier que R et Machine Learning Services existent dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2bd9e43232b77bc77611b0c4cd5285b69c9a6261
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046820"
---
# <a name="quickstart-verify-r-exists-in-sql-server"></a>Démarrage rapide : Vérifiez que R existe dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server inclut la prise en charge du langage R pour l’analytique de science des données sur les données de SQL Server résidentes. Votre script R peut être constitué des fonctions R open source, des bibliothèques R de tiers ou des bibliothèques de Microsoft R intégrés tel que [RevoScaleR](../r/revoscaler-overview.md) pour l’analytique prédictive à l’échelle.

L’exécution du script est via des procédures stockées, à l’aide d’une des approches suivantes :

+ Intégrés [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) procédure stockée, en passant dans un script R comme paramètre d’entrée.
+ Encapsuler le script R dans un [procédure stockée personnalisée](sqldev-in-database-r-for-sql-developers.md) que vous créez.

Dans ce démarrage rapide, vous allez vérifier que [SQL Server 2017 Machine Learning Services](../what-is-sql-server-machine-learning.md) ou [SQL Server 2016 R Services](../r/sql-server-r-services.md) est installé et configuré.

## <a name="prerequisites"></a>Prérequis

Cet exercice requiert l’accès à une instance de SQL Server avec l’un des déjà installé les composants suivants :

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), avec le langage R installé
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

Votre instance SQL Server peut être dans une machine virtuelle Azure ou en local. Soyez conscient que la fonctionnalité de script externe est désactivée par défaut, vous devrez donc peut-être à [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifiez que **service SQL Server Launchpad** est en cours d’exécution avant de commencer.

Vous devez également un outil pour l’exécution de requêtes SQL. Vous pouvez exécuter les scripts R à l’aide d’une gestion de base de données ou interroger l’outil, tant qu’il peut se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-r-exists"></a>Vérifiez que R existe

Vous pouvez vérifier que les Services Machine Learning (avec R) est activé pour votre instance de SQL Server et la version de R est installée. Suivez les étapes ci-dessous.

1. Ouvrez SQL Server Management Studio et connectez-vous à votre instance de SQL Server.

2. Exécutez le code ci-dessous. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'R',
    @script=N'print(version)';
    GO
    ```

3. R `print` fonction retourne la version à la **Messages** fenêtre. Dans l’exemple ci-dessous, vous pouvez voir que SQL Server que dans ce cas R version 3.3.3 installé.

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

Si vous obtenez des erreurs à partir de cette requête, éliminer tout problème d’installation. Configuration de post-installation est nécessaire pour permettre l’utilisation des bibliothèques de code externe. Consultez [installer SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) ou [installer SQL Server 2016 R Services](../install/sql-r-services-windows-install.md). De même, assurez-vous que le service Launchpad est en cours d’exécution.

Selon votre environnement, vous pouvez être amené à activer les comptes de travail R pour vous connecter à SQL Server, installer des bibliothèques réseau supplémentaires, activer l’exécution de code à distance ou redémarrer l’instance une fois que tout est configuré. Pour plus d’informations, consultez [Installation de R Services et de mettre à niveau le Forum aux questions](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="list-r-packages"></a>Liste R packages

Microsoft fournit un nombre de packages R préinstallés avec Machine Learning Services dans votre instance de SQL Server. Pour afficher la liste de R packages installés, y compris la version, les dépendances, les licences et les informations de chemin d’accès de bibliothèque, suivez les étapes ci-dessous.

1. Exécutez le script ci-dessous sur votre instance de SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
    OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
    WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
        , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
    ```

2. La sortie est à partir de `installed.packages()` dans R et retournée comme résultat ensemble.

    **Résultats**

    ![Les packages installés dans R](./media/rsql-installed-packages.png)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez confirmé que votre instance est prêt à travailler avec R, examinons plus en détail une interaction R de base.

> [!div class="nextstepaction"]
> [Démarrage rapide : Script R « Hello world » dans SQL Server ](quickstart-r-run-using-tsql.md)
