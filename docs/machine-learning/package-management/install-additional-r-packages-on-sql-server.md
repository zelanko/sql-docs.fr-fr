---
title: Installer de nouveaux packages R
description: Découvrez comment utiliser sqlmlutils pour installer de nouveaux packages R sur une instance de SQL Server Machine Learning Services ou SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/20/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ff2d40dab5fa2d8f03bf3d1fa32b08e66a0ccdbc
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81118112"
---
# <a name="install-new-r-packages-with-sqlmlutils"></a>Installer de nouveaux packages R avec sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit comment utiliser des fonctions du package [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils) pour installer de nouveaux packages R sur une instance de SQL Server Machine Learning Services ou SQL Server R Services. Les packages que vous installez peuvent être utilisés dans des scripts R exécutés dans la base de données à l’aide de l’instruction T-SQL [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

> [!NOTE]
> La commande `install.packages` R standard n’est pas recommandée pour l’ajout de packages R sur SQL Server. Au lieu de cela, utilisez **sqlmlutils** comme décrit dans cet article.

## <a name="prerequisites"></a>Conditions préalables requises

- Installez [R](https://www.r-project.org) et [RStudio Desktop](https://www.rstudio.com/products/rstudio/download/) sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server. Vous pouvez utiliser n’importe quel IDE R pour exécuter les scripts, mais cet article part du principe que vous utilisez RStudio.

- Installez [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) ou [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server. Vous pouvez utiliser d’autres outils de gestion de base de données ou de requête, mais cet article part du principe que vous utilisez Azure Data Studio ou SSMS.

### <a name="other-considerations"></a>Autres considérations

- Le script R s’exécutant dans SQL Server peut utiliser uniquement des packages installés dans la bibliothèque d’instances par défaut. SQL Server ne peut pas charger les packages à partir de bibliothèques externes, même si cette bibliothèque est sur le même ordinateur. Cela comprend les bibliothèques R installées avec d’autres produits Microsoft.

- Dans un environnement SQL Server renforcé, vous souhaiterez peut-être éviter ce qui suit :
  - Les packages qui nécessitent un accès réseau
  - Les packages qui nécessitent un accès au système de fichiers élevé
  - Les packages utilisés pour le développement Web ou d’autres tâches qui ne bénéficient pas de l’exécution dans SQL Server

## <a name="install-sqlmlutils-on-the-client-computer"></a>Installer sqlmlutils sur l’ordinateur client

Pour utiliser **sqlmlutils**, vous devez d’abord l’installer sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server.

Le package **sqlmlutils** dépend du package **RODBCext**, et **RODBCext** dépend d’un certain nombre d’autres packages. Les procédures suivantes installent tous ces packages dans le bon ordre.

### <a name="install-sqlmlutils-online"></a>Installer sqlmlutils en ligne

Si l’ordinateur client a accès à Internet, vous pouvez télécharger et installer **sqlmlutils** et ses packages dépendants en ligne.

1. Téléchargez le dernier fichier zip **sqlmlutils** à partir de https://github.com/Microsoft/sqlmlutils/tree/master/R/dist sur l’ordinateur client. Ne décompressez pas le fichier.

1. Ouvrez une **invite de commandes** et exécutez les commandes suivantes pour installer les packages **sqlmlutils** et **RODBCext**. Remplacez le chemin d’accès complet par le fichier zip **sqlmlutils** que vous avez téléchargé (cet exemple suppose que le fichier se trouve dans votre dossier Documents). Le package **RODBCext** est trouvé en ligne et installé.

   ```console
   R -e "install.packages('RODBCext', repos='https://cran.microsoft.com')"
   R CMD INSTALL %UserProfile%\Documents\sqlmlutils_0.7.1.zip
   ```

### <a name="install-sqlmlutils-offline"></a>Installer sqlmlutils hors connexion

Si l’ordinateur client n’a pas de connexion Internet, vous devez télécharger les packages **sqlmlutils** et **RODBCext** à l’avance à l’aide d’un ordinateur qui a accès à Internet. Vous pouvez ensuite copier les fichiers dans un dossier sur l’ordinateur client et installer les packages hors connexion.

Le package **RODBCext** contient un certain nombre de packages dépendants, et l’identification de toutes les dépendances d’un package devient compliquée. Nous vous recommandons d’utiliser [**miniCRAN**](https://andrie.github.io/miniCRAN/) pour créer un dossier de référentiel local pour le package qui comprend tous les packages dépendants.
Pour plus d’informations, consultez [Créer un référentiel de packages R local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).

Le package **sqlmlutils** se compose d’un seul fichier zip que vous pouvez copier sur l’ordinateur client et installer.

Sur un ordinateur connecté à Internet :

1. Installez **miniCRAN**. Pour plus d’informations, consultez [Installer miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran).

1. Dans RStudio, exécutez le script R suivant pour créer un référentiel local du package **RODBCext**. Cet exemple crée le référentiel dans le dossier `c:\downloads\rodbcext`.

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/rodbcext"
   pkgs_needed <- "RODBCext"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end

   Pour la valeur `Rversion`, utilisez la version de R installée sur SQL Server. Pour vérifier la version installée, utilisez la commande T-SQL suivante.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Téléchargez le dernier fichier zip **sqlmlutils** à partir de [https://github.com/Microsoft/sqlmlutils/tree/master/R/dist](https://github.com/Microsoft/sqlmlutils/tree/master/R/dist) (ne décompressez pas le fichier). Par exemple, téléchargez le fichier dans `c:\downloads\sqlmlutils_0.7.1.zip`.

1. Copiez la totalité du dossier du référentiel **RODBCext** (`c:\downloads\rodbcext`) et le fichier zip **sqlmlutils** (`c:\downloads\sqlmlutils_0.7.1.zip`) sur l’ordinateur client. Par exemple, copiez-les dans le dossier `c:\temp\packages` sur l’ordinateur client.

Sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server, ouvrez une invite de commandes et exécutez les commandes suivantes pour installer **RODBCext** puis **sqlmlutils**.

```console
R -e "install.packages('RODBCext', repos='c:\temp\packages\rodbcext')"
R CMD INSTALL c:\temp\packages\sqlmlutils_0.7.1.zip
```

## <a name="add-an-r-package-on-sql-server"></a>Ajouter un package R sur SQL Server

Dans l’exemple suivant, vous allez ajouter le package [**glue**](https://cran.r-project.org/web/packages/glue/) à SQL Server.

### <a name="add-the-package-online"></a>Ajouter le package en ligne

Si l’ordinateur client que vous utilisez pour vous connecter à SQL Server a accès à Internet, vous pouvez utiliser **sqlmlutils** pour rechercher le package **glue** et toutes les dépendances sur Internet, puis installer le package sur une instance SQL Server à distance.

1. Sur l’ordinateur client, ouvrez RStudio et créez un fichier de **script R**.

1. Utilisez le script R suivant pour installer le package**glue** à l’aide de **sqlmlutils**. Remplacez les valeurs existantes par vos propres informations de connexion à la base de données SQL Server.

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server   = "server",
     database = "database",
     uid      = "username",
     pwd      = "password")

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC")
   ```

   > [!TIP]
   > La valeur **scope** (étendue) peut être définie sur **PUBLIC** ou **PRIVATE**. L’étendue publique est utile pour que l’administrateur de base de données puisse installer des packages que tous les utilisateurs peuvent utiliser. L’étendue privée rend le package disponible uniquement pour l’utilisateur qui l’installe. Si vous ne spécifiez pas l’étendue, l’étendue par défaut est définie sur **PRIVÉE**.

### <a name="add-the-package-offline"></a>Ajouter le package hors connexion

Si l’ordinateur client n’a pas de connexion Internet, vous pouvez utiliser **miniCRAN** pour télécharger le package**glue** à l’aide d’un ordinateur qui a accès à Internet. Vous copiez ensuite le package sur l’ordinateur client sur lequel vous pouvez installer le package hors connexion.
Consultez [Installer miniCRAN](create-a-local-package-repository-using-minicran.md#install-minicran) pour plus d’informations sur l’installation de **miniCRAN**.

Sur un ordinateur connecté à Internet :

1. Exécutez le script R suivant pour créer un référentiel local pour **glue**. Cet exemple crée le dossier du référentiel dans `c:\downloads\glue`.

   ::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.5");
   ```

   ::: moniker-end

   ::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

   ```R
   CRAN_mirror <- c(CRAN = "https://cran.microsoft.com")
   local_repo <- "c:/downloads/glue"
   pkgs_needed <- "glue"
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);

   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "source", Rversion = "3.5");
   ```

   ::: moniker-end


   Pour la valeur `Rversion`, utilisez la version de R installée sur SQL Server. Pour vérifier la version installée, utilisez la commande T-SQL suivante.

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(R.version)'
   ```

1. Copiez l’intégralité du dossier du référentiel **glue** (`c:\downloads\glue`) sur l’ordinateur client. Par exemple, copiez-le dans le dossier `c:\temp\packages\glue`.

Sur l’ordinateur client :

1. Ouvrez RStudio et créez un fichier de **script R**.

1. Utilisez le script R suivant pour installer le package**glue** à l’aide de **sqlmlutils**. Remplacez vos propres informations de connexion de base de données SQL Server (si vous n’utilisez pas l’authentification Windows, ajoutez les paramètres `uid` et `pwd`).

   ```R
   library(sqlmlutils)
   connection <- connectionInfo(
     server= "yourserver",
     database = "yourdatabase")
   localRepo = "c:/temp/packages/glue"

   sql_install.packages(connectionString = connection, pkgs = "glue", verbose = TRUE, scope = "PUBLIC", repos=paste0("file:///",localRepo))
   ```

   > [!TIP]
   > La valeur **scope** (étendue) peut être définie sur **PUBLIC** ou **PRIVATE**. L’étendue publique est utile pour que l’administrateur de base de données puisse installer des packages que tous les utilisateurs peuvent utiliser. L’étendue privée rend le package disponible uniquement pour l’utilisateur qui l’installe. Si vous ne spécifiez pas l’étendue, l’étendue par défaut est définie sur **PRIVÉE**.

## <a name="use-the-package"></a>Utiliser le package

Une fois le package **glue** installé, vous pouvez l’utiliser dans un script R dans SQL Server à l’aide de la commande T-SQL **sp_execute_external_script**.

1. Ouvrez Azure Data Studio ou SSMS et connectez-vous à votre base de données SQL Server.

1. Exécutez la commande suivante :

   ```sql
   EXECUTE sp_execute_external_script @language = N'R'
       , @script = N'
   library(glue)

   name <- "Fred"
   birthday <- as.Date("2020-06-14")
   text <- glue(''My name is {name} '',
   ''and my birthday is {format(birthday, "%A, %B %d, %Y")}.'')

   print(text)
         ';
   ```

    **Résultats**

    ```text
    My name is Fred and my birthday is Sunday, June 14, 2020.
    ```

## <a name="remove-the-package"></a>Supprimer le package

Si vous souhaitez supprimer le package **glue**, exécutez le script R suivant. Utilisez la même variable de **connexion** que celle que vous avez définie précédemment.

```R
sql_remove.packages(connectionString = connection, pkgs = "glue", scope = "PUBLIC")
```

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les packages R installés, consultez [Récupérer les informations du package R](r-package-information.md)
- Pour obtenir de l’aide sur l’utilisation des packages R, consultez [Conseils pour l’utilisation de packages R](tips-for-using-r-packages.md)
- Pour plus d’informations sur l’installation des packages Python, consultez [Installer des packages Python avec sqlmlutils](install-additional-python-packages-on-sql-server.md)
- Pour plus d’informations sur SQL Server Machine Learning Services, consultez [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
