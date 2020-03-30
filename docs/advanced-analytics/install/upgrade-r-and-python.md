---
title: Mise à niveau des éléments R et Python
description: Mettez à niveau R et Python dans SQL Server Machine Learning Services ou SQL Server R Services à l’aide de sqlbindr.exe pour établir une liaison avec Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: abc14f78a969abd4adbbb2dcf12b4ee316614d23
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69634549"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Mettre à niveau les composants Machine Learning (R et Python) dans les instances SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’intégration de R et Python dans SQL Server comprend des packages open source et des packages propriétaires Microsoft. Dans le cadre de la maintenance SQL Server standard, les packages sont mis à jour conformément au cycle de publication de SQL Server, avec des correctifs de bogues pour les packages existants de la version actuelle, mais sans mise à niveau de la version principale. 

Toutefois, de nombreux scientifiques de données sont habitués à travailler avec des packages plus récents lorsqu’ils sont disponibles. Pour SQL Server Machine Learning Services (dans la base de données) et SQL Server R Services (dans la base de données), vous pouvez obtenir des [versions plus récentes de R et de Python](#version-map) en *créant une liaison* avec **Microsoft Machine Learning Server**. 

## <a name="what-is-binding"></a>Qu’est-ce qu’une liaison ?

La liaison est un processus d’installation qui permute le contenu de vos dossiers R_SERVICES et PYTHON_SERVICES avec des fichiers exécutables, des bibliothèques et des outils plus récents de [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).

Dans les modèles de maintenance, les composants mis à jour s’accompagnent d’un commutateur. Au lieu du [cycle de vie du produit SQL Server](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017), avec les [mises à jour cumulatives de SQL Server](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions), vos mises à jour de service sont désormais conformes à la [chronologie de prise en charge pour Microsoft R Server et Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) du [de cycle de vie moderne](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

À l’exception des versions de composant et des mises à jour de service, la liaison ne modifie pas les bases de votre installation : L’intégration R et Python fait toujours partie d’une instance de moteur de base de données, la gestion des licences demeure inchangée (aucun coût supplémentaire associé à la liaison) et les politiques de prise en charge de SQL Server restent valables pour le moteur de base de données. Le reste de cet article décrit le mécanisme de liaison et son fonctionnement pour chaque version de SQL Server.

> [!NOTE]
> La liaison s’applique uniquement aux instances (dans la base de données) qui sont liées à des instances SQL Server. La liaison ne concerne pas les installations (autonomes).

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
**Considérations relatives à la liaison SQL Server 2017**

Pour SQL Server Machine Learning Services, envisagez une liaison uniquement lorsque Microsoft Machine Learning Server commence à proposer des packages supplémentaires ou des versions plus récentes que celle dont vous disposez déjà.
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**Considérations relatives à la liaison SQL Server 2016**

Pour les clients SQL Server 2016 R Services, la liaison fournit des packages R mis à jour, de nouveaux packages qui ne font pas partie de l’installation d’origine ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)) et des [modèles pré-entraînés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models). Tous ces éléments peuvent être actualisés à chaque nouvelle version principale et secondaire de [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index). La liaison n’assure pas la prise en charge de Python, qui est une fonctionnalité SQL Server 2017.
::: moniker-end

<a name="version-map"></a>

## <a name="version-map"></a>Mappage de version

Le tableau suivant est un mappage de version. Il présente les versions de packages sur les différentes versions publiées, afin que vous puissiez déterminer les chemins de mise à niveau potentiels lorsque vous établissez une liaison à Microsoft Machine Learning Server (anciennement R Server, avant l’ajout de la prise en charge de Python à partir de MLS 9.2.1). 

Notez que la liaison ne garantit pas de disposer de la dernière version de R ou d’Anaconda. Lorsque vous établissez une liaison à Microsoft Machine Learning Server (MLS), vous disposez de la version R ou Python installée via le programme d’installation. Il peut donc s’agir d’une version différente de la dernière version disponible sur le Web.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Composant |Version initiale | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) sur R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9,1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.0.1 |  9,1 |  9.2.1 |  9.3 |
[modèles pré-entraînés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| n.a. | 9.0.1 |  9,1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
[**SQL Server Machine Learning Services**](../install/sql-machine-learning-services-windows-install.md)

Composant |Version initiale | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) sur R | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4.2 sur Python 3.5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[modèles pré-entraînés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |
::: moniker-end

## <a name="how-component-upgrade-works"></a>Fonctionnement de la mise à niveau des composants 

Les bibliothèques et les exécutables R et Python sont mis à niveau lorsque vous liez une installation existante de R et Python à Machine Learning Server. La liaison est exécutée par le [programme d’installation Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) lorsque vous l’exécutez sur une instance de moteur de base de données SQL Server existante disposant de l’intégration R ou Python. Le programme d’installation détecte les fonctionnalités existantes et vous invite à effectuer une nouvelle liaison avec Machine Learning Server. 

Au cours de la liaison, le contenu de `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES` et `\PYTHON_SERVICES` est remplacé par les nouveaux exécutables et les nouvelles bibliothèques de `C:\Program Files\Microsoft\ML Server\R_SERVER` et de `\PYTHON_SERVER`.

Dans le même temps, le modèle de maintenance évolue également. Il passe des mécanismes de mise à jour de SQL Server au cycle de version principale et secondaire le plus fréquent de Microsoft Machine Learning Server. Le changement de politique de prise en charge est une option intéressante pour les équipes de science des données dont les solutions nécessitent des modules R et Python nouvelle génération. 

+ Sans liaison, les packages R et Python reçoivent des correctifs de bogues lors de l’installation d’un Service Pack ou d’une mise à jour cumulative SQL Server. 
+ Avec la liaison, il est possible d’appliquer des versions de package plus récentes sur votre instance, indépendamment du calendrier de publication des mises à jour cumulatives, conformément à la [politique de cycle de vie moderne](https://support.microsoft.com/help/30881/modern-lifecycle-policy) et aux versions de Microsoft Machine Learning Server. La politique de prise en charge du cycle de vie moderne offre des mises à jour plus fréquentes pendant une durée d’un an. Après la liaison, vous continuerez à utiliser le programme d’installation de MLS pour les futures mises à jour de R et de Python lorsqu’elles seront mises à disposition sur les sites de téléchargement Microsoft.

La liaison s’applique uniquement aux fonctionnalités R et Python, c’est-à-dire aux packages open source pour les fonctionnalités R et Python (Microsoft R Open, Anaconda) et aux packages propriétaires RevoScaleR, revoscalepy, etc. La liaison ne modifie pas le modèle de prise en charge pour l’instance du moteur de base de données, ni la version de SQL Server.

La liaison est réversible. Vous pouvez rétablir la maintenance SQL Server en [dissociant l’instance](#bkmk_Unbind) et en réparant votre instance de moteur de base de données SQL Server.

En résumé, les étapes de liaison sont les suivantes :

+ Utilisez une installation existante et configurée de SQL Server R Services ou SQL Server Machine Learning Services.
+ Déterminez quelle version de Microsoft Machine Learning Server dispose des composants mis à niveau que vous souhaitez utiliser.
+ Téléchargez et exécutez le programme d’installation de cette version. Le programme d’installation détecte l’instance existante, ajoute une option de liaison et renvoie une liste d’instances compatibles.
+ Choisissez l’instance que vous souhaitez lier, puis terminez le programme d’installation pour exécuter la liaison.

En termes d’expérience utilisateur, la technologie et la façon dont vous l’utilisez restent inchangées. La seule différence réside dans la présence de packages d’une version plus récente et éventuellement de packages supplémentaires qui n’étaient pas disponibles à l’origine par le biais de SQL Server.

## <a name="bind-to-mls-using-setup"></a><a name="bkmk_BindWizard"></a>Lier à MLS à l’aide du programme d’installation

Le programme d’installation de Microsoft Machine Learning détecte les fonctionnalités existantes et la version de SQL Server, avant d’appeler un utilitaire nommé SqlBindR.exe pour modifier la liaison. En interne, SqlBindR est chaîné au programme d’installation et utilisé indirectement. Vous avez la possibilité d’appeler SqlBindR ultérieurement, directement à partir de la ligne de commande, pour exercer des options spécifiques.

1. Dans SSMS, exécutez `SELECT @@version` pour vérifier que le serveur répond aux conditions minimales requises pour la build. 

   Pour SQL Server 2016 R Services, vous devez disposez au minimum du [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) et de la mise à jour cumulative [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Vérifiez la version des packages R Base et RevoScaleR pour vous assurer que les versions existantes sont inférieures à celles par lesquelles vous envisagez de les remplacer. 

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

1. Fermez SSMS et tous les autres outils disposant d’une connexion ouverte à SQL Server. La liaison remplace les fichiers programme. Si des sessions SQL Server sont ouvertes, la liaison échoue avec le code d’erreur de liaison 6.

1. Téléchargez Microsoft Machine Learning Server sur l’ordinateur hébergeant l’instance que vous souhaitez mettre à niveau. Nous vous recommandons de télécharger la [version la plus récente](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Décompressez le dossier et lancez ServerSetup.exe, sous MLSWIN93.

   ![Assistant d’installation Microsoft Machine Learning Server](media/mls-921-installer-start.PNG)

1. Sur l’écran **Configurer l’installation**, confirmez les composants à mettre à niveau et passez en revue la liste des instances compatibles. 

   Cette étape est très importante.

   Sur la gauche, choisissez toutes les fonctionnalités à conserver ou à mettre à niveau. Vous ne pouvez pas mettre à niveau certaines fonctionnalités seulement. Une case à cocher vide supprime la fonctionnalité correspondante, en supposant qu’elle est actuellement installée. Dans la capture d’écran, à partir d’une instance de SQL Server 2016 R Services (MSSQL13), R et la version R des modèles pré-entraînés sont sélectionnés. Cette configuration est valide, car SQL Server 2016 prend en charge R, mais pas Python.

   Si vous mettez à niveau des composants sur SQL Server 2016 R Services, ne sélectionnez pas la fonctionnalité Python. Vous ne pouvez pas ajouter Python à SQL Server 2016 R Services.

   Sur la droite, cochez la case en regard du nom de l’instance. Si aucune instance n’est répertoriée, cela signifie que votre combinaison n’est pas compatible. Si vous ne sélectionnez aucune instance, une nouvelle installation autonome de Machine Learning Server est créée, et les bibliothèques SQL Server restent inchangées. Si vous ne pouvez pas sélectionner une instance, il se peut qu’elle ne se trouve pas sur [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Étape de configuration de l’installation](media/mls-931-installer-mssql13.png)

1. Sur la page **Contrat de licence**, sélectionnez **J’accepte ces termes** pour accepter les termes du contrat de licence de Machine Learning Server. 

1. Sur les pages suivantes, donnez votre accord pour les conditions de licence supplémentaires de tous les composants open source que vous avez sélectionnés, tels que Microsoft R Open ou la distribution Python Anaconda.

1. Sur la page **Vous y êtes presque**, prenez note du dossier d’installation. Le dossier par défaut est : \Program Files\Microsoft\ML Server.

    Si vous souhaitez modifier le dossier d’installation, cliquez sur **Avancé** pour revenir à la première page de l’assistant. Toutefois, vous devez dans ce cas répéter toutes les sélections précédentes.

Pendant le processus d’installation, toutes les bibliothèques R ou Python utilisées par SQL Server sont remplacées et Launchpad est mis à jour pour utiliser les composants les plus récents. Par conséquent, si l’instance utilisait par le passé des bibliothèques dans le dossier R_SERVICES par défaut, après la mise à niveau, ces bibliothèques sont supprimées et les propriétés du service Launchpad sont modifiées pour utiliser les bibliothèques au nouvel emplacement.

La liaison affecte le contenu de ces dossiers : C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library est remplacé par le contenu du dossier C:\Program Files\Microsoft\ML Server\R_SERVER. Le deuxième dossier et son contenu sont créés par le programme d’installation de Microsoft Machine Learning Server. 

Si la mise à niveau échoue, consultez les [codes d’erreur SqlBindR](#sqlbindr-error-codes) pour plus d’informations.

## <a name="confirm-binding"></a>Confirmer la liaison

Vérifiez de nouveau la version de R et de RevoScaleR pour vous assurer que vous disposez de versions plus récentes. Utilisez la console R distribuée avec les packages R dans votre instance de moteur de base de données pour récupérer les informations sur le package :

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

Pour SQL Server 2016 R Services lié à Machine Learning Server 9.3, la version du package R Base doit être 3.4.3 et la version de RevoScaleR doit être 9.3. Vous devez en outre disposer de MicrosoftML 9.3. 

Si vous avez ajouté les modèles pré-entraînés, ceux-ci sont incorporés dans la bibliothèque MicrosoftML et vous pouvez les appeler par le biais de fonctions MicrosoftML. Pour plus d’informations, consultez les [exemples R pour MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Liaison hors connexion (pas d’accès Internet)

Pour les systèmes qui ne sont pas connectés à Internet, vous pouvez télécharger le programme d’installation et les fichiers .cab sur un ordinateur connecté à Internet, puis transférer ces fichiers vers le serveur isolé. 

Le programme d’installation (ServerSetup.exe) inclut les packages Microsoft (RevoScaleR, MicrosoftML, olapr, sqlRUtils). Les fichiers .cab fournissent les autres composants de base. Par exemple, le fichier .cab « SRO » fournit R Open, la distribution Microsoft de R open source.

Les instructions suivantes expliquent comment placer les fichiers pour une installation hors connexion.

1. Téléchargez le programme d’installation MLS. Il est téléchargé en tant que fichier zip unique. Nous vous recommandons d’utiliser la [dernière version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), mais vous pouvez également installer les [versions antérieures](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Téléchargez les fichiers .cab. Les liens suivants concernent la version 9.3. Si vous avez besoin des versions antérieures, vous trouverez des liens supplémentaires dans [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Rappelez-vous que Python/Anaconda peut uniquement être ajouté à une instance Machine Learning Services SQL Server. Des modèles pré-entraînés existent pour R et Python ; le fichier .cab fournit les modèles dans les langages que vous utilisez.

    | Fonctionnalité | Téléchargement |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Modèles dont l’apprentissage a déjà été effectué | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Transférez les fichiers .zip et .cab vers le serveur cible.

1. Sur le serveur, tapez `%temp%` dans la commande Exécuter pour récupérer l’emplacement physique du répertoire temporaire. Le chemin d’accès physique varie en fonction de l’ordinateur, mais il est généralement `C:\Users\<your-user-name>\AppData\Local\Temp`.

1. Placez les fichiers .cab dans le dossier %temp%.

1. Décompressez le programme d’installation.

1. Exécutez le fichier ServerSetup.exe et suivez les invites à l’écran pour terminer l’installation.

## <a name="command-line-operations"></a><a name="bkmk_BindCmd"></a>Opérations de ligne de commande

Après avoir exécuté Microsoft Machine Learning Server, un utilitaire de ligne de commande appelé SqlBindR.exe devient disponible. Vous pouvez l’utiliser pour d’autres opérations de liaison. Par exemple, si vous décidez d’inverser une liaison, vous pouvez soit réexécuter le programme d’installation, soit utiliser l’utilitaire de ligne de commande. Vous pouvez également utiliser cet outil pour vérifier la compatibilité et la disponibilité des instances.

> [!TIP]
> Vous ne trouvez pas SqlBindR ? Vous n’avez probablement pas exécuté le programme d’installation. SqlBindR est disponible uniquement après l’exécution du programme d’installation de Machine Learning Server.

1. Ouvrez une invite de commandes en tant qu’administrateur et accédez au dossier contenant sqlbindr.exe. L’emplacement par défaut est : C:\Program Files\Microsoft\MLServer\Setup.

2. Tapez la commande suivante pour afficher la liste des instances disponibles : `SqlBindR.exe /list`
  
   Notez le nom complet de l’instance tel qu’il est répertorié. Par exemple, le nom de l’instance peut être MSSQL14.MSSQLSERVER pour une instance par défaut, ou un nom de type NOMSERVEUR.MONINSTANCENOMMÉE.

3. Exécutez la commande **SqlBindR.exe** avec l’argument */bind*, puis spécifiez le nom de l’instance à mettre à niveau en utilisant le nom de l’instance tel qu’il est renvoyé à l’étape précédente.

   Par exemple, pour mettre à niveau l’instance par défaut, tapez : `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Une fois la mise à niveau terminée, redémarrez le service Launchpad associé à l’instance qui a été modifiée.

## <a name="revert-or-unbind-an-instance"></a><a name="bkmk_Unbind"></a>Rétablir ou annuler la liaison d’une instance

Vous pouvez restaurer une instance liée vers une installation initiale des composants R et Python, établie par le programme d’installation de SQL Server. Pour revenir à la maintenance SQL Server, vous devez suivre trois étapes.

+ [Étape 1 : Annuler la liaison à Microsoft Machine Learning Server](#step-1-unbind)
+ [Étape 2 : Restaurer l’état d’origine de l’instance](#step-2-restore)
+ [Étape 3 : Réinstaller tous les packages que vous aviez ajoutés à l’installation](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Étape 1 : Annuler la liaison

Vous avez deux options pour restaurer la liaison : réexécuter la configuration ou utiliser l’utilitaire de ligne de commande SqlBindR.

#### <a name="unbind-using-setup"></a><a name="bkmk_wizunbind"></a> Annulation de la liaison à l’aide du programme d’installation

1. Localisez le programme d’installation de Machine Learning Server. Si vous avez supprimé le programme d’installation, vous devrez peut-être le télécharger de nouveau ou le copier à partir d’un autre ordinateur.
2. Assurez-vous d’exécuter le programme d’installation sur l’ordinateur hébergeant l’instance que vous souhaitez séparer.
2. Le programme d’installation identifie les instances locales qui sont candidates pour l’annulation de la liaison.
3. Décochez la case en regard de l’instance pour laquelle vous souhaitez restaurer la configuration d’origine.
4. Acceptez le contrat de licence. Vous devez confirmer que vous acceptez les termes du contrat de licence, y compris lors de l’installation.
5. Cliquez sur **Terminer**. Le processus prend un certain temps.

#### <a name="unbind-using-the-command-line"></a><a name="bkmk_cmdunbind"></a> Annulation de la liaison à l’aide de la ligne de commande

1. Ouvrez une invite de commandes et accédez au dossier qui contient **sqlbindr.exe**, comme décrit dans la section précédente.

2. Exécutez la commande **SqlBindR.exe** avec l’argument */unbind*, puis spécifiez l’instance.

   Par exemple, la commande suivante rétablit l’instance par défaut :
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Étape 2 : Réparer l’instance SQL Server

Exécutez le programme d’installation de SQL Server pour réparer l’instance du moteur de base de données qui héberge les fonctionnalités R et Python. Les mises à jour existantes sont conservées, mais si vous avez manqué des mises à jour de maintenance SQL Server pour les packages R et Python, cette étape applique ces correctifs.

Cela nécessite davantage d’implication, mais vous pouvez également désinstaller et réinstaller complètement l’instance du moteur de base de données, puis appliquer toutes les mises à jour du service.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Étape 3 : Ajouter des packages tiers

Vous aviez peut-être ajouté d’autres packages tiers ou open source à votre bibliothèque de packages. Étant donné que l’inversion de la liaison modifie l’emplacement de la bibliothèque de packages par défaut, vous devez réinstaller les packages dans la bibliothèque que R et Python utilisent désormais. Pour plus d’informations, consultez les [informations sur les packages R](../package-management/r-package-information.md) et [leur installation](../package-management/install-additional-r-packages-on-sql-server.md), ainsi que les [informations sur les packages Python](../package-management/python-package-information.md) et [leur installation](../package-management/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>Syntaxe de commande SqlBindR.exe

### <a name="usage"></a>Usage

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Paramètres

|Nom|Description|
|------|------|
|*list*| Affiche une liste de tous les ID d’instances de bases de données SQL sur l’ordinateur actuel|
|*bind*| Met à niveau l’instance de base de données SQL spécifiée vers la version la plus récente de R Server, et garantit que l’instance obtient automatiquement les mises à niveau ultérieures de R Server|
|*unbind*|Désinstalle la version la plus récente de R Server de l’instance de base de données SQL spécifiée, et empêche les mises à niveau ultérieures de R Server d’affecter l’instance|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Erreurs de liaison

Le programme d’installation de MLS et SqlBindR renvoient les codes d’erreur et messages suivants.

|Code d'erreur  | Message           | Détails               |
|------------|-------------------|-----------------------|
|Erreur de liaison 0 | Ok (succès) | La liaison a réussi sans erreur. |
|Erreur de liaison 1 | Arguments non valides | Erreur de syntaxe. |
|Erreur de liaison 2 | Action non valide | Erreur de syntaxe. |
|Erreur de liaison 3 | Instance non valide | Une instance existe, mais elle n’est pas valide pour la liaison. |
|Erreur de liaison 4 | Ne peut pas être lié | |
|Erreur de liaison 5 | Déjà lié | Vous avez exécuté la commande *bind* , mais l’instance spécifiée est déjà liée. |
|Erreur de liaison 6 | Échec de la liaison | Une erreur est survenue lors de l’annulation de la liaison de l’instance. Cette erreur peut se produire si vous exécutez le programme d’installation de MLS sans sélectionner de fonctionnalités. Pour la liaison, vous devez sélectionner à la fois une instance MSSQL et R et Python, en supposant que l’instance soit SQL Server 2017. Cette erreur se produit également si SqlBindR n’a pas pu écrire dans le dossier Program Files. Les sessions ouvertes ou les descripteurs vers SQL Server provoquent cette erreur. Si vous voyez cette erreur, redémarrez l’ordinateur et recommencez les étapes de liaison avant de démarrer de nouvelles sessions.|
|Erreur de liaison 7 | Non lié | L’instance du moteur de base de données héberge R Services ou SQL Server Machine Learning Services. L’instance n’est pas liée à Microsoft Machine Learning Server. |
|Erreur de liaison 8 | Échec de l’annulation de la liaison | Une erreur est survenue lors de l’annulation de la liaison de l’instance. |
|Erreur de liaison 9 | Aucune instance trouvée | Aucune instance du moteur de base de données n’a été trouvée sur cet ordinateur. |

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie les problèmes connus spécifiques à l’utilisation de l’utilitaire SqlBindR.exe, ou aux mises à niveau de Machine Learning Server susceptibles d’affecter des instances SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Restauration des packages précédemment installés

Si vous avez effectué une mise à niveau vers Microsoft R Server 9.0.1, la version de SqlBindR.exe pour cette version n’a pas pu restaurer complètement les packages d’origine ou les composants R. L’utilisateur doit réparer SQL Server sur l’instance, appliquer toutes les versions de service, puis redémarrer l’instance.

La version ultérieure de SqlBindR restaure automatiquement les fonctionnalités R d’origine, ce qui évite d’avoir à réinstaller les composants R ou à réappliquer les correctifs au serveur. Toutefois, vous devez installer toutes les mises à jour du package R qui ont pu être ajoutées après l’installation initiale.

Si vous avez utilisé les rôles de gestion des packages pour installer et partager des packages, cette tâche est beaucoup plus facile : vous pouvez utiliser des commandes R pour synchroniser les packages installés sur le système de fichiers à l’aide des enregistrements de la base de données, et vice versa. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../r/install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Problèmes avec les mises à niveau multiples à partir de SQL Server

Si vous avez déjà mis à niveau une instance de SQL Server 2016 R Services vers la version 9.0.1, lorsque vous exécutez le nouveau programme d’installation pour Microsoft R Server 9.1.0, il affiche une liste de toutes les instances valides, puis sélectionne par défaut les instances précédemment liées. Si vous continuez, la liaison des instances précédemment liées est annulée. Par conséquent, la version 9.0.1 antérieure est désinstallée, y compris tous les packages associés, mais la nouvelle version de Microsoft R Server (9.1.0) n’est pas installée.

Pour résoudre ce problème, vous pouvez modifier l’installation R Server existante comme suit :
1. Dans le Panneau de configuration, ouvrez **Ajout/Suppression de programmes**.
2. Recherchez Microsoft R Server, puis cliquez sur **Modifier**.
3. Au démarrage du programme d’installation, sélectionnez les instances que vous souhaitez lier à la version 9.1.0.

Microsoft Machine Learning Server 9.2.1 et 9.3 ne présentent pas ce problème.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>La liaison ou l’annulation d’une liaison laisse plusieurs dossiers temporaires

Parfois, les opérations de liaison et d’annulation de liaison ne parviennent pas à nettoyer les dossiers temporaires.
Si vous trouvez des dossiers avec un nom ressemblant au suivant, vous pouvez le supprimer une fois l’installation terminée : R_SERVICES_<guid>

> [!NOTE]
> Veillez à patienter jusqu’à la fin de l’installation. La suppression des bibliothèques R associées à une version et l’ajout des nouvelles bibliothèques R peuvent prendre longtemps. Une fois l’opération terminée, les dossiers temporaires sont supprimés.

## <a name="see-also"></a>Voir aussi

+ [Installer Machine Learning Server pour Windows (connecté à Internet)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installer Machine Learning Server pour Windows (hors connexion)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Problèmes connus dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Annonces de fonctionnalités de la version précédente de R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Fonctionnalités déconseillées, supprimées ou modifiées](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
