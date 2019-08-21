---
title: Récupérer les informations du package R
description: Apprenez à obtenir des informations sur les packages R installés sur SQL Server Machine Learning Services et SQL Server R Services.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 8c3cf3c1debc03c169c585521b8b46dd8b1365c5
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69641156"
---
# <a name="get-r-package-information"></a>Récupérer les informations du package R

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment obtenir des informations sur les packages R installés sur SQL Server Machine Learning Services et SQL Server R Services. Les exemples de scripts R vous montrent comment répertorier des informations de package telles que le chemin d’installation et la version.

## <a name="default-r-library-location"></a>Emplacement de la bibliothèque R par défaut

Lorsque vous installez Machine Learning avec SQL Server, une seule bibliothèque de packages est créée au niveau de l’instance pour chaque langue que vous installez. Sur Windows, la bibliothèque d’instances est un dossier sécurisé enregistré avec SQL Server.

Tout script qui s’exécute dans la base de données sur SQL Server doit charger les fonctions à partir de la bibliothèque d’instances. SQL Server ne pouvez pas accéder aux packages installés dans d’autres bibliothèques. Cela s’applique également aux clients distants: tout script R s’exécutant dans le contexte de calcul du serveur ne peut utiliser que des packages installés dans la bibliothèque d’instances.
Pour protéger les ressources du serveur, la bibliothèque d’instances par défaut ne peut être modifiée que par un administrateur de l’ordinateur.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Le chemin d’accès par défaut des binaires pour R est le suivant:

`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Le chemin d’accès par défaut des binaires pour R est le suivant:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Le chemin d’accès par défaut des binaires pour R est le suivant:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

Cela suppose l’instance SQL par défaut, MSSQLSERVER. Si SQL Server est installé en tant qu’instance nommée définie par l’utilisateur, le nom donné est utilisé à la place.

<!-- I don't think this note is necessary. If you have these other products installed, you'd already know about them.
> [!NOTE]
> If you find other folders having similar subfolder names and files, you probably have a standalone installation of  Microsoft R Server or Machine Learning Server. These server products have different installers and paths: C:\Program Files\Microsoft\R Server\R_SERVER or C:\Program Files\Microsoft\ML SERVER\R_SERVER. For more information, see [Install R Server 9.1 for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) or [Install Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).
-->

Exécutez l’instruction suivante pour vérifier la bibliothèque de packages R par défaut pour l’instance actuelle:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

L’instruction suivante utilise [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) pour retourner le chemin d’accès de la bibliothèque d’instances et la version de RevoScaleR utilisée par SQL Server:

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> La fonction [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) ne peut être exécutée que sur l’ordinateur local. La fonction ne peut pas retourner de chemins d’accès de bibliothèque pour les connexions à distance.

## <a name="default-r-packages"></a>Packages R par défaut

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

Les packages R suivants sont installés avec SQL Server R Services.

|. | Version | Description |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | Utilisé pour les contextes de calcul distants, la diffusion en continu et l’exécution parallèle des fonctions RX pour l’importation et la transformation des données, la modélisation, la visualisation et l’analyse. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | Utilisé pour inclure le script R dans les procédures stockées. |

::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"

Les packages R suivants sont installés avec SQL Server Machine Learning Services lorsque vous sélectionnez la fonctionnalité R lors de l’installation.

|. | Version | Description |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 9,2 | Utilisé pour les contextes de calcul distants, la diffusion en continu et l’exécution parallèle des fonctions RX pour l’importation et la transformation des données, la modélisation, la visualisation et l’analyse. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 9,2 | Utilisé pour inclure le script R dans les procédures stockées. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| 9,2 | Ajoute des algorithmes de Machine Learning dans R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 9,2 | Utilisé pour écrire des instructions MDX dans R. |

::: moniker-end

### <a name="component-upgrades"></a>Mises à niveau de composants

Par défaut, les packages R sont actualisés par le biais des service packs et des mises à jour cumulatives. Les packages supplémentaires et les mises à niveau de version complète des composants de base de R ne sont possibles que par le biais de mises à niveau de produit ou par liaison de la prise en charge de R à Microsoft Machine Learning Server.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
En outre, vous pouvez ajouter des packages MicrosoftML et olapr à une instance de SQL Server à l’aide d’une mise à niveau de composant.
::: moniker-end

Pour plus d’informations, consultez [mettre à niveau les composants R et Python dans SQL Server](../install/upgrade-r-and-python.md).

## <a name="default-open-source-r-packages"></a>Packages R Open source par défaut

La prise en charge de r comprend Open-source afin que vous puissiez appeler des fonctions R de base et installer des packages Open source et tiers supplémentaires. La prise en charge du langage R comprend des fonctionnalités principales telles que la **base**, les **statistiques**, les **utils**et d’autres. Une installation de base de R comprend également un grand nombre d’exemples de jeux de données et d’outils R standard tels que **RGui** (un éditeur interactif léger) et **RTerm** (une invite de commandes r).

La distribution du R Open source inclus dans votre installation est [Microsoft R Open (MRO)](https://mran.microsoft.com/open). MRO ajoute de la valeur à base R en incluant des packages Open source supplémentaires, tels que la [bibliothèque de noyaux mathématiques Intel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
La version de R fournie par MRO à l’aide du programme d’installation de SQL Server R Services est 3.2.2.
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
La version de R fournie par MRO à l’aide de SQL Server Machine Learning Services le programme d’installation est 3.3.3.
::: moniker-end

> [!IMPORTANT]
> Vous ne devez jamais remplacer manuellement la version de R installée par SQL Server installation avec des versions plus récentes sur le Web. Les packages Microsoft R sont basés sur des versions spécifiques de R. la modification de votre installation pourrait le déstabiliser.

## <a name="list-all-installed-r-packages"></a>Répertorier tous les packages R installés

L’exemple suivant utilise la fonction `installed.packages()` r dans une [!INCLUDE[tsql](../../includes/tsql-md.md)] procédure stockée pour afficher une liste des packages R qui ont été installés dans la bibliothèque R_SERVICES pour l’instance SQL actuelle. Ce script retourne les champs nom et version du package dans le fichier de DESCRIPTION.

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);',
@input_data_1 = N'
  '
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Pour plus d’informations sur les champs facultatifs et par défaut du champ DESCRIPTION du package [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)R, consultez.

## <a name="find-a-single-r-package"></a>Rechercher un package R unique

Si vous avez installé un package R et que vous souhaitez vous assurer qu’il est disponible pour une instance de SQL Server particulière, vous pouvez exécuter une procédure stockée pour charger le package et renvoyer des messages.

Par exemple, l’instruction suivante recherche et charge le package [Glue](https://cran.r-project.org/web/packages/glue/) , s’il est disponible.
Si le package est introuvable ou ne peut pas être chargé, vous recevez une erreur contenant le texte «il n’y a aucun package appelé «glue».»

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("glue")'
GO
```

Pour plus d’informations sur le package, `packageDescription`consultez.
L’instruction suivante retourne des informations pour le package de **Collage** .

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("glue"))
  '
```

## <a name="next-steps"></a>Étapes suivantes

+ [Installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md)
+ [Recevoir des informations sur le package Python](python-package-information.md)
+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Didacticiels R et Python](../tutorials/machine-learning-services-tutorials.md)
