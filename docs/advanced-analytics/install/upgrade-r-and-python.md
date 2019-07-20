---
title: Mettre à niveau les composants R et Python
description: Mettez à niveau R et Python dans SQL Server services 2016 ou SQL Server 2017 Machine Learning Services à l’aide de sqlbindr. exe pour établir une liaison à Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: def007433075920e419f0bf77be5977d1145f793
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344962"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Mettre à niveau les composants Machine Learning (R et Python) dans les instances de SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’intégration de R et Python dans SQL Server comprend des packages Open source et des packages propriétaires de Microsoft. Dans le cadre de la maintenance des SQL Server standard, les packages sont mis à jour conformément au cycle de publication de SQL Server, avec des correctifs de bogues pour les packages existants à la version actuelle, mais aucune mise à niveau majeure de la version. 

Toutefois, de nombreux scientifiques de données sont habitués à travailler avec des packages plus récents lorsqu’ils sont disponibles. Pour les SQL Server 2017 Machine Learning Services (dans la base de données) et SQL Server les services 2016 R (dans la base de données), vous pouvez obtenir [des versions plus récentes de r et Python](#version-map) en les *liant* à **Microsoft machine learning Server**. 

## <a name="what-is-binding"></a>Qu’est-ce que la liaison?

La liaison est un processus d’installation qui permute le contenu de vos dossiers R_SERVICES et PYTHON_SERVICES avec des fichiers exécutables, des bibliothèques et des outils plus récents à partir de [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/index).

Les composants mis à jour intègrent un commutateur dans les modèles de maintenance. Au lieu du [cycle de vie du produit SQL Server](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017), avec [SQL Server mises à jour cumulatives](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions), vos mises à jour de service sont désormais conformes à la [chronologie du support pour Microsoft R Server & machine learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) sur le [cycle de vie moderne](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

À l’exception des versions de composant et des mises à jour de service, la liaison ne modifie pas les notions de base de votre installation: L’intégration R et Python fait toujours partie d’une instance du moteur de base de données, la gestion des licences est inchangée (aucun coût supplémentaire associé à la liaison) et SQL Server stratégies de prise en charge sont toujours valables pour le moteur de base de données. Le reste de cet article décrit le mécanisme de liaison et son fonctionnement pour chaque version de SQL Server.

> [!NOTE]
> La liaison s’applique aux instances (dans la base de données) uniquement liées à des instances de SQL Server. La liaison n’est pas pertinente pour une installation (autonome).

**Considérations relatives à la liaison SQL Server 2017**

Pour SQL Server 2017 Machine Learning Services, vous pouvez envisager une liaison uniquement lorsque Microsoft Machine Learning Server commence à proposer des packages supplémentaires ou des versions plus récentes que vous avez déjà.

**Considérations relatives à la liaison SQL Server 2016**

Pour les clients SQL Server R 2016 R services, la liaison fournit des packages R mis à jour, de nouveaux packages qui ne font pas partie de l’installation d’origine ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)) et des [modèles](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)préformés, qui peuvent tous être actualisés à chaque nouvelle version majeure et mineure de [Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/index). La liaison ne vous offre pas la prise en charge de Python, qui est une fonctionnalité SQL Server 2017. 

<a name="version-map"></a>

## <a name="version-map"></a>Mappage de version

Le tableau suivant est une carte de version, qui présente les versions de packages sur les différentes versions des véhicules afin que vous puissiez déterminer les chemins de mise à niveau potentiels lorsque vous établissez une liaison à Microsoft Machine Learning Server (anciennement R Server, avant l’ajout de la prise en charge de Python en cours de démarrage dans MLS 9.2.1). 

Notez que la liaison ne garantit pas la dernière version de R ou Anaconda. Lorsque vous établissez une liaison à Microsoft Machine Learning Server (MLS), vous recevez la version R ou python installée via le programme d’installation, qui peut ne pas être la dernière version disponible sur le Web.

[**SQL Server 2016 R services**](../install/sql-r-services-windows-install.md)

Composant |Version initiale | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9,1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9,3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) sur R | R 3.2.2     | R 3.3.2   |R 3.3.3   | O 3.4.1  | 3\.4.3 R |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[modèles préformés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| n.a. | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a. | 1.0 |  1.0 |  1.0 |  1.0 |


[**SQL Server 2017 Machine Learning Services**](../install/sql-machine-learning-services-windows-install.md)

Composant |Version initiale | MLS 9,3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) sur R | R 3.3.3 | 3\.4.3 R | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9,2 |  9,3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9,2  | 9,3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4,2 sur Python 3,5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2  | 9,3| | | |
 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2  | 9,3| | | |
[modèles préformés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9,2 | 9,3| | | |

## <a name="how-component-upgrade-works"></a>Fonctionnement de la mise à niveau des composants 

Les bibliothèques et les exécutables r et Python sont mis à niveau lorsque vous liez une installation existante de R et Python à Machine Learning Server. La liaison est exécutée par le [programme d’installation de Microsoft machine learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) lorsque vous exécutez le programme d’installation sur une instance de moteur de base de données SQL Server existante, 2016 ou 2017, avec l’intégration R ou python. Le programme d’installation détecte les fonctionnalités existantes et vous invite à effectuer une liaison à Machine Learning Server. 

Au cours de la liaison, le contenu de C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES et \PYTHON_SERVICES sont remplacés par les fichiers exécutables et les bibliothèques les plus récents de C:\Program Files\Microsoft\ML Server\R_SERVER et \PYTHON_SERVER.

En même temps, le modèle de maintenance est également retournée des mécanismes de mise à jour de SQL Server, vers le cycle de version principale et secondaire le plus fréquent de Microsoft Machine Learning Server. Le changement de stratégie de support est une option intéressante pour les équipes de science des données qui nécessitent des modules R et Python plus récents pour leurs solutions. 

+ Sans liaison, les packages R et Python sont corrigés pour les correctifs de bogues lors de l’installation d’un SQL Server Service Pack ou d’une mise à jour cumulative (CU). 
+ Avec la liaison, des versions de package plus récentes peuvent être appliquées à votre instance, indépendamment du calendrier de publication CU, sous la [stratégie de cycle de vie moderne](https://support.microsoft.com/help/30881/modern-lifecycle-policy) et les versions de Microsoft machine learning Server. La politique de support du cycle de vie moderne offre des mises à jour plus fréquentes pendant une durée de vie d’un an. Après la liaison, vous continuerez à utiliser le programme d’installation de MLS pour les futures mises à jour de R et Python, car elles seront disponibles sur les sites de téléchargement Microsoft.

La liaison s’applique uniquement aux fonctionnalités R et Python. À savoir, les packages Open source pour les fonctionnalités R et Python (Microsoft R Open, Anaconda) et les packages propriétaires RevoScaleR, revoscalepy, et ainsi de suite. La liaison ne modifie pas le modèle de prise en charge pour l’instance du moteur de base de données et ne modifie pas la version de SQL Server.

La liaison est réversible. Vous pouvez rétablir SQL Server maintenance en annulant [la liaison de l’instance](#bkmk_Unbind) et en reparing votre SQL Server instance du moteur de base de données.

En résumé, les étapes de liaison sont les suivantes:

+ Commencez avec une installation existante configurée de SQL Server 2016 R services (ou SQL Server 2017 Machine Learning Services).
+ Déterminez la version de Microsoft Machine Learning Server qui contient les composants mis à niveau que vous souhaitez utiliser.
+ Téléchargez et exécutez le programme d’installation de cette version. Le programme d’installation détecte l’instance existante, ajoute une option de liaison et retourne une liste d’instances compatibles.
+ Choisissez l’instance que vous souhaitez lier, puis terminez le programme d’installation pour exécuter la liaison.

En termes d’expérience utilisateur, la technologie et la façon dont vous l’utilisez sont inchangées. La seule différence réside dans la présence de packages avec version plus récente et éventuellement de packages supplémentaires non disponibles à l’origine par le biais de SQL Server (par exemple, MicrosoftML pour les clients SQL Server R 2016 R).

## <a name="bkmk_BindWizard"></a>Lier à MLS à l’aide du programme d’installation

Le programme d’installation de Microsoft Machine Learning détecte les fonctionnalités existantes et les SQL Server version et appelle un utilitaire appelé SqlBindR. exe pour modifier la liaison. En interne, SqlBindR est chaîné à la configuration et utilisé indirectement. Plus tard, vous pouvez appeler SqlBindR directement à partir de la ligne de commande pour exercer des options spécifiques.

1. Dans SSMS, exécutez `SELECT @@version` pour vérifier que le serveur répond aux exigences de build minimales. 

   Pour les services SQL Server R 2016, le minimum est [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) et [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Vérifiez la version des packages R base et RevoScaleR pour vous assurer que les versions existantes sont inférieures à celles que vous envisagez de les remplacer. Pour SQL Server R 2016 R services, le package de base R est 3.2.2 et RevoScaleR est 8.0.3.

    ```sql
    EXECUTE sp_execute_external_script
    @language=N'R'
    ,@script = N'str(OutputDataSet);
    packagematrix <- installed.packages();
    Name <- packagematrix[,1];
    Version <- packagematrix[,3];
    OutputDataSet <- data.frame(Name, Version);'
    , @input_data_1 = N''
    WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
    ```

1. Fermez SSMS et tous les autres outils disposant d’une connexion ouverte à SQL Server. La liaison remplace les fichiers programme. Si SQL Server possède des sessions ouvertes, la liaison échoue avec le code d’erreur de liaison 6.

1. Téléchargez Microsoft Machine Learning Server sur l’ordinateur disposant de l’instance que vous souhaitez mettre à niveau. Nous vous recommandons d’utiliser la [dernière version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Décompressez le dossier et démarrez Server. exe, situé sous MLSWIN93.

   ![Assistant Installation de Microsoft Machine Learning Server](media/mls-921-installer-start.PNG)

1. Dans **configurer l’installation**, confirmez les composants à mettre à niveau et passez en revue la liste des instances compatibles. 

   Cette étape est très importante.

   Sur la gauche, choisissez toutes les fonctionnalités que vous souhaitez conserver ou mettre à niveau. Vous ne pouvez pas mettre à niveau certaines fonctionnalités et pas d’autres. Une case à cocher vide supprime cette fonctionnalité, en supposant qu’elle est actuellement installée. Dans la capture d’écran, à partir d’une instance de SQL Server 2016 R services (MSSQL13), R et la version R des modèles préformés sont sélectionnées. Cette configuration est valide, car SQL Server 2016 prend en charge R, mais pas python.

   Si vous mettez à niveau des composants sur SQL Server les services R 2016, ne sélectionnez pas la fonctionnalité Python. Vous ne pouvez pas ajouter Python à SQL Server 2016 R services.

   Sur la droite, activez la case à cocher en regard du nom de l’instance. Si aucune instance n’est répertoriée, vous avez une combinaison incompatible. Si vous ne sélectionnez pas une instance, une nouvelle installation autonome de Machine Learning Server est créée, et les bibliothèques de SQL Server sont inchangées. Si vous ne pouvez pas sélectionner une instance, il se peut qu’elle ne se trouve pas à l’adresse [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Configurer l’étape d’installation](media/mls-931-installer-mssql13.png)

1. Sur la page **contrat de licence** , sélectionnez **J’accepte les termes** du contrat de licence pour machine learning Server. 

1. Sur des pages successives, fournissez un consentement à des conditions de licence supplémentaires pour tous les composants Open source que vous avez sélectionnés, tels que Microsoft R Open ou la distribution Python Anaconda.

1. Dans la page qui **s’y trouve presque** , notez le dossier d’installation. Le dossier par défaut est \Program Files\Microsoft\ML Server.

    Si vous souhaitez modifier le dossier d’installation, cliquez sur **avancé** pour revenir à la première page de l’Assistant. Toutefois, vous devez répéter toutes les sélections précédentes.

Pendant le processus d’installation, toutes les bibliothèques R ou python utilisées par SQL Server sont remplacées et Launchpad est mis à jour pour utiliser les composants les plus récents. Par conséquent, si l’instance utilisait précédemment des bibliothèques dans le dossier R_SERVICES par défaut, après la mise à niveau, ces bibliothèques sont supprimées et les propriétés du service Launchpad sont modifiées pour utiliser les bibliothèques dans le nouvel emplacement.

La liaison affecte le contenu de ces dossiers: C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library est remplacé par le contenu de C:\Program Files\Microsoft\ML Server\R_SERVER. Le deuxième dossier et son contenu sont créés par le programme d’installation de Microsoft Machine Learning Server. 

Si la mise à niveau échoue, vérifiez les [codes d’erreur SqlBindR](#sqlbindr-error-codes) pour plus d’informations.

## <a name="confirm-binding"></a>Confirmer la liaison

Revérifiez la version de R et RevoScaleR pour vous assurer que vous disposez de versions plus récentes. Utilisez la console R distribuée avec les packages R dans votre instance du moteur de base de données pour récupérer les informations du package:

```sql
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Par SQL Server 2016 R services liés à Machine Learning Server 9,3, le package R de base doit être 3.4.3, RevoScaleR doit être 9,3 et MicrosoftML 9,3 doit également être installé. 

Si vous avez ajouté les modèles préformés, les modèles sont incorporés dans la bibliothèque MicrosoftML et vous pouvez les appeler par le biais de fonctions MicrosoftML. Pour plus d’informations, consultez [exemples R pour MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Liaison hors connexion (pas d’accès Internet)

Pour les systèmes sans connectivité Internet, vous pouvez télécharger les fichiers du programme d’installation et. cab sur un ordinateur connecté à Internet, puis transférer des fichiers vers le serveur isolé. 

Le programme d’installation (Server. exe) comprend les packages Microsoft (RevoScaleR, MicrosoftML, olapr, sqlRUtils). Les fichiers. cab fournissent d’autres composants principaux. Par exemple, le fichier CAB «SRO» fournit R Open, la distribution Microsoft de R Open source.

Les instructions suivantes expliquent comment placer les fichiers pour une installation hors connexion.

1. Téléchargez le programme d’installation de MLS. Il est téléchargé en tant que fichier zippé unique. Nous vous recommandons d’utiliser la [version la plus récente](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), mais vous pouvez également installer des [versions antérieures](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Téléchargez les fichiers. cab. Les liens suivants concernent la version 9,3. Si vous avez besoin de versions antérieures, vous trouverez des liens supplémentaires dans [R Server 9,1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Rappelez-vous que Python/Anaconda peut uniquement être ajouté à une instance SQL Server 2017 Machine Learning Services. Des modèles préformés existent pour R et Python; le fichier. cab fournit des modèles dans les langages que vous utilisez.

    | Fonctionnalité | Télécharger |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Modèles dont l’apprentissage a déjà été effectué | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Transférez les fichiers. zip et. cab sur le serveur cible.

1. Sur le serveur, tapez `%temp%` la commande exécuter pour récupérer l’emplacement physique du répertoire temporaire. Le chemin d’accès physique varie en fonction de l’ordinateur `C:\Users\<your-user-name>\AppData\Local\Temp`, mais il s’agit généralement de.

1. Placez les fichiers. cab dans le dossier% Temp%.

1. Décompressez le programme d’installation.

1. Exécutez Server. exe et suivez les invites à l’écran pour terminer l’installation.

## <a name="bkmk_BindCmd"></a>Opérations de ligne de commande

Après avoir exécuté Microsoft Machine Learning Server, un utilitaire de ligne de commande appelé SqlBindR. exe devient disponible et vous pouvez l’utiliser pour d’autres opérations de liaison. Par exemple, si vous décidez d’inverser une liaison, vous pouvez soit réexécuter le programme d’installation, soit utiliser l’utilitaire de ligne de commande. En outre, vous pouvez utiliser cet outil pour vérifier la compatibilité et la disponibilité des instances.

> [!TIP]
> SqlBindR introuvable? Vous n’avez probablement pas exécuté le programme d’installation. SqlBindR est disponible uniquement après l’exécution du programme d’installation de Machine Learning Server.

1. Ouvrez une invite de commandes en tant qu’administrateur et accédez au dossier contenant sqlbindr.exe. L’emplacement par défaut est C:\Program Files\Microsoft\MLServer\Setup

2. Tapez la commande suivante pour afficher la liste des instances disponibles : `SqlBindR.exe /list`
  
   Notez le nom complet de l’instance tel qu’il est répertorié. Par exemple, le nom de l’instance peut être MSSQL14. MSSQLSERVER pour une instance par défaut, ou un nom de type SERVERNAME. MYNAMEDINSTANCE.

3. Exécutez la commande **SqlBindR. exe** avec l’argument */Bind* et spécifiez le nom de l’instance à mettre à niveau, en utilisant le nom de l’instance qui a été retourné à l’étape précédente.

   Par exemple, pour mettre à niveau l’instance par défaut, tapez:`SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Une fois la mise à niveau terminée, redémarrez le service Launchpad associé à une instance qui a été modifiée.

## <a name="bkmk_Unbind"></a>Rétablir ou annuler la liaison d’une instance

Vous pouvez restaurer une instance liée à une installation initiale des composants R et Python, établie par SQL Server installation. Il y a trois parties pour revenir au SQL Server maintenance.

+ [Étape 1 : Dissocier de Microsoft Machine Learning Server](#step-1-unbind)
+ [Étape 2 : Restaurer l’état d’origine de l’instance](#step-2-restore)
+ [Étape 3 : Réinstaller tous les packages que vous avez ajoutés à l’installation](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Étape 1 : Séparer

Vous avez deux options pour restaurer la liaison: réexécutez la configuration ou utilisez l’utilitaire de ligne de commande SqlBindR.

#### <a name="bkmk_wizunbind"></a>Séparer à l’aide du programme d’installation

1. Localisez le programme d’installation de Machine Learning Server. Si vous avez supprimé le programme d’installation, vous devrez peut-être le télécharger à nouveau ou le copier à partir d’un autre ordinateur.
2. Veillez à exécuter le programme d’installation sur l’ordinateur qui contient l’instance que vous souhaitez dissocier.
2. Le programme d’installation identifie les instances locales qui sont candidates pour la dissociation.
3. Désactivez la case à cocher en regard de l’instance que vous souhaitez restaurer dans la configuration d’origine.
4. Acceptez le contrat de licence. Vous devez indiquer votre acceptation des termes du contrat de licence même lors de l’installation de.
5. Cliquez sur **Terminer**. Le processus prend un certain temps.

#### <a name="bkmk_cmdunbind"></a>Annuler la liaison à l’aide de la ligne de commande

1. Ouvrez une invite de commandes et accédez au dossier qui contient **sqlbindr.exe**, comme décrit dans la section précédente.

2. Exécutez la commande **SqlBindR.exe** avec l’argument */unbind*, puis spécifiez l’instance.

   Par exemple, la commande suivante rétablit l’instance par défaut:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Étape 2 : Réparer l’instance de SQL Server

Exécutez le programme d’installation de SQL Server pour réparer l’instance du moteur de base de données avec les fonctionnalités R et Python. Les mises à jour existantes sont conservées, mais si vous avez manqué des mises à jour de SQL Server de maintenance des packages R et Python, cette étape applique ces correctifs.

Cela est également plus professionnel, mais vous pouvez également désinstaller et réinstaller complètement l’instance du moteur de base de données, puis appliquer toutes les mises à jour du service.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Étape 3 : Ajouter des packages tiers

Vous avez peut-être ajouté d’autres packages Open source ou tiers à votre bibliothèque de packages. Étant donné que l’inversion de la liaison change l’emplacement de la bibliothèque de package par défaut, vous devez réinstaller les packages dans la bibliothèque que R et Python utilisent désormais. Pour plus d’informations, consultez [packages par défaut](../package-management/default-packages.md), [installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md)et [installer de nouveaux packages python](../python/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>Syntaxe de commande SqlBindR. exe

### <a name="usage"></a>Utilisation

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Paramètres

|Nom|Description|
|------|------|
|*list*| Affiche une liste de tous les ID d’instances de bases de données SQL sur l’ordinateur actuel|
|*bind*| Met à niveau l’instance de base de données SQL spécifiée vers la version la plus récente de R Server, et garantit que l’instance obtient automatiquement les mises à niveau ultérieures de R Server|
|*unbind*|Désinstalle la version la plus récente de R Server de l’instance de base de données SQL spécifiée, et empêche les mises à niveau ultérieures de R Server d’affecter l’instance|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Erreurs de liaison

Le programme d’installation de MLS et SqlBindR retournent les codes d’erreur et les messages suivants.

|Code d'erreur  | `Message`           | Détails               |
|------------|-------------------|-----------------------|
|Erreur de liaison 0 | OK (réussite) | La liaison a réussi sans erreurs. |
|Erreur de liaison 1 | Arguments non valides | Erreur de syntaxe. |
|Erreur de liaison 2 | Action non valide | Erreur de syntaxe. |
|Erreur de liaison 3 | Instance non valide | Une instance existe, mais n’est pas valide pour la liaison. |
|Erreur de liaison 4 | Non pouvant être lié | |
|Erreur de liaison 5 | Déjà lié | Vous avez exécuté la commande *bind* , mais l’instance spécifiée est déjà liée. |
|Erreur de liaison 6 | Échec de la liaison | Une erreur s’est produite lors de la dissociation de l’instance. Cette erreur peut se produire si vous exécutez le programme d’installation de MLS sans sélectionner de fonctionnalités. Pour la liaison, vous devez sélectionner à la fois une instance MSSQL et R et Python, en supposant que l’instance est SQL Server 2017. Cette erreur se produit également si SqlBindR n’a pas pu écrire dans le dossier Program Files. Les sessions ouvertes ou les descripteurs à SQL Server provoquent cette erreur. Si vous recevez cette erreur, redémarrez l’ordinateur et recommencez les étapes de liaison avant de démarrer les nouvelles sessions.|
|Erreur de liaison 7 | Non lié | L’instance du moteur de base de données contient R services ou SQL Server Machine Learning Services. L’instance n’est pas liée à Microsoft Machine Learning Server. |
|Erreur de liaison 8 | Échec de la dissociation | Une erreur s’est produite lors de la dissociation de l’instance. |
|Erreur de liaison 9 | Aucune instance trouvée | Aucune instance du moteur de base de données n’a été trouvée sur cet ordinateur. |

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie les problèmes connus spécifiques à l’utilisation de l’utilitaire SqlBindR. exe, ou les mises à niveau de Machine Learning Server susceptibles d’affecter des instances de SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Restauration des packages précédemment installés

Si vous avez effectué une mise à niveau vers Microsoft R Server version9.0.1, la version de SqlBindR. exe pour cette version n’a pas pu restaurer complètement les packages d’origine ou les composants R, ce qui nécessite que l’utilisateur exécute SQL Server réparation sur l’instance, applique toutes les versions de service, puis redémarre instance de.

La version ultérieure de SqlBindR restaure automatiquement les fonctionnalités R d’origine, ce qui évite d’avoir à réinstaller les composants R ou à réappliquer les correctifs au serveur. Toutefois, vous devez installer toutes les mises à jour du package R qui ont pu être ajoutées après l’installation initiale.

Si vous avez utilisé les rôles de gestion des packages pour installer et partager des packages, cette tâche est beaucoup plus facile: vous pouvez utiliser des commandes R pour synchroniser les packages installés sur le système de fichiers à l’aide des enregistrements de la base de données, et vice versa. Pour plus d’informations, consultez [gestion des packages R pour SQL Server](../r/install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Problèmes avec plusieurs mises à niveau à partir de SQL Server

Si vous avez déjà mis à niveau une instance de SQL Server 2016 R services vers la version 9.0.1, lorsque vous exécutez le nouveau programme d’installation pour Microsoft R Server 9.1.0, il affiche une liste de toutes les instances valides, puis sélectionne par défaut les instances précédemment liées. Si vous continuez, les instances précédemment liées sont détachées. Par conséquent, l’installation de la version 9.0.1 antérieure est supprimée, y compris tous les packages associés, mais la nouvelle version de Microsoft R Server (9.1.0) n’est pas installée.

Pour résoudre ce problème, vous pouvez modifier l’installation R Server existante comme suit:
1. Dans le panneau de configuration, ouvrez **Ajout/suppression de programmes**.
2. Recherchez Microsoft R Server, puis cliquez sur **modifier/modifier**.
3. Au démarrage du programme d’installation, sélectionnez les instances que vous souhaitez lier à 9.1.0.

Microsoft Machine Learning Server 9.2.1 et 9,3 n’ont pas ce problème.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>La liaison ou la dissociation quitte plusieurs dossiers temporaires

Parfois, les opérations de liaison et d’annulation de liaison ne parviennent pas à nettoyer les dossiers temporaires.
Si vous trouvez des dossiers avec un nom tel que celui-ci, vous pouvez le supprimer une fois l’installation terminée: R_SERVICES_<guid>

> [!NOTE]
> Veillez à patienter jusqu’à la fin de l’installation. La suppression des bibliothèques R associées à une version peut prendre beaucoup de temps, puis ajouter les nouvelles bibliothèques R. Une fois l’opération terminée, les dossiers temporaires sont supprimés.

## <a name="see-also"></a>Voir aussi

+ [Installer Machine Learning Server pour Windows (connecté à Internet)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installer Machine Learning Server pour Windows (hors connexion)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Problèmes connus dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Annonces de fonctionnalités de la version précédente de R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Fonctionnalités dépréciées, supprimées ou modifiées](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
