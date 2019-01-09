---
title: Mettre à niveau les composants R et Python - SQL Server Machine Learning Services
description: Mise à niveau R et Python dans SQL Server 2016 Services ou SQL Server 2017 Machine Learning Services à l’aide de sqlbindr.exe pour lier à Machine Learning Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 897f83e7272a47428d696802adf79ff816805486
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645448"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Mettre à niveau machine learning (R et Python) des composants dans les instances SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Intégration de R et Python dans SQL Server inclut les packages open source et le propriétaire de Microsoft. Sous maintenance de SQL Server standard, les packages sont mis à jour selon le cycle de publication SQL Server, avec les correctifs de bogues pour les packages existants depuis la version actuelle, mais aucune mise à niveau de version principale. 

Toutefois, nombreux scientifiques de données sont habitués à travailler avec des packages plus récents dès qu’elles sont disponibles. Pour SQL Server 2017 Machine Learning Services (en base de données) et SQL Server 2016 R Services (en base de données), vous pouvez obtenir [des versions plus récentes de R et Python](#version-map) par *liaison* à **Microsoft Machine Learning Server**. 

## <a name="what-is-binding"></a>Ce qui est la liaison ?

Liaison est un processus d’installation qui remplace le contenu de vos dossiers R_SERVICES et PYTHON_SERVICES avec des exécutables plus récente, bibliothèques et des outils à partir de [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index).

Avec composants mis à jour est fourni à un commutateur dans les modèles de maintenance. Au lieu du [cycle de vie de produit SQL Server](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017), avec [mises à jour cumulatives de SQL Server](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions), vos mises à jour de service est désormais conforme à la [prise en charge de la chronologie de l’ordinateur & Microsoft R Server Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) sur le [cycle de vie moderne](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

À l’exception des versions des composants et les mises à jour de service, liaison ne modifie pas les notions de base de votre installation : Intégration de R et Python fait toujours partie d’une instance de moteur de base de données, Gestionnaire de licences n’est pas affecté (aucun coût supplémentaire associé aux liaisons) et les stratégies de prise en charge de SQL Server contiennent toujours pour le moteur de base de données. Le reste de cet article explique le mécanisme de liaison et son fonctionnement pour chaque version de SQL Server.

> [!NOTE]
> Liaison s’applique aux instances (en base de données) uniquement qui sont liés aux instances de SQL Server. Liaison n’est pas pertinente pour une installation (autonome).

**Considérations relatives à la liaison SQL Server 2017**

Pour SQL Server 2017 Machine Learning Services aurait-elle liaison uniquement lorsque Microsoft Machine Learning Server commence à offrir des packages supplémentaires ou des versions plus récentes sur ce que vous ont déjà.

**Considérations relatives à la liaison SQL Server 2016**

Pour les clients SQL Server 2016 R Services, liaison fournit des packages R mis à jour, de nouveaux packages ne fait pas partie de l’installation d’origine ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)), et [modèles préformés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models), qui peut être davantage actualisées à chaque nouvelle version majeure et mineure de [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index). Liaison ne donne pas une prise en charge de Python, qui est une fonctionnalité de SQL Server 2017. 

<a name="version-map"></a>

## <a name="version-map"></a>Mappage de version

Le tableau suivant est un mappage de version, affichage des versions de package sur les véhicules de version afin que vous pouvez déterminer les chemins de mise à niveau potentiels lorsque vous liez à Microsoft Machine Learning Server (anciennement R Server, avant l’ajout de prise en charge de Python à partir dans MLS 9.2.1). 

Notez que liaison ne garantit pas la version récente de R ou Anaconda. Lorsque vous liez à Microsoft Machine Learning Server (SIA), vous obtenez la version de R ou Python installée via la configuration, qui ne peut être la dernière version disponible sur le web.

[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Composant |Version initiale | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) sur R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | version 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| (pays-bas) | version 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[modèles préformés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| (pays-bas) | version 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| (pays-bas) | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | (pays-bas) | 1.0 |  1.0 |  1.0 |  1.0 |


[**SQL Server 2017 Machine Learning Services**](../install/sql-machine-learning-services-windows-install.md)

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
[modèles préformés](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |

## <a name="how-component-upgrade-works"></a>Fonctionne de la mise à niveau du composant 

Fichiers exécutables et les bibliothèques R et Python sont mis à niveau lorsque vous liez une installation existante de R et Python à Machine Learning Server. Liaison est exécutée par le [programme d’installation de Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) lorsque vous exécutez le programme d’installation sur une instance SQL Server existante de base de données du moteur, 2016 ou 2017, avec intégration de R ou Python. Le programme d’installation détecte les fonctionnalités existantes et vous invite à relier à Machine Learning Server. 

Lors de la liaison, le contenu de C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES et \PYTHON_SERVICES est remplacé par les fichiers exécutables et les bibliothèques de C:\Program Files\Microsoft\ML Server\R_SERVER et \PYTHON_SERVER plus récente.

En même temps, le modèle de maintenance est également retourné à partir de mécanismes de mise à jour de SQL Server, sur le cycle de version majeure et mineure plus fréquent de Microsoft Machine Learning Server. Stratégies de prise en charge de commutation est une option intéressante pour les équipes de science des données qui ont besoin de nouvelle génération R et les modules de Python pour leurs solutions. 

+ Sans liaison, les packages R et Python sont corrigés pour corriger les bogues lorsque vous installez un service pack SQL Server ou la mise à jour cumulative (CU). 
+ La liaison de versions plus récentes de package peuvent être appliquées à votre instance, indépendamment de la planification de la version CU, sous la [politique de cycle de vie moderne](https://support.microsoft.com/help/30881/modern-lifecycle-policy) et les versions de Microsoft Machine Learning Server. La politique de support du cycle de vie moderne offre des mises à jour plus fréquentes sur une durée de vie plus courte d’un an. Après la liaison, vous continuent à utiliser le programme d’installation MLS pour les mises à jour ultérieures de R et Python qu’elles sont disponibles sur les sites de téléchargement Microsoft.

Liaison s’applique aux fonctionnalités de R et Python uniquement. À savoir, les packages open source pour les fonctionnalités de R et Python (Microsoft R Open, Anaconda) et les propriétaires packages RevoScaleR, revoscalepy et ainsi de suite. Liaison ne change pas le modèle de prise en charge pour l’instance du moteur de base de données et ne change pas la version de SQL Server.

La liaison est réversible. Vous pouvez revenir à la maintenance de SQL Server par [la séparation de l’instance](#bkmk_Unbind) et réparer votre instance de moteur de base de données SQL Server.

Étapes pour la liaison totalisée, sont les suivantes :

+ Démarrez avec une installation existante, configurée de SQL Server 2016 R Services (ou SQL Server 2017 Machine Learning Services).
+ Déterminer quelle version de Microsoft Machine Learning Server possède les composants mis à niveau que vous souhaitez utiliser.
+ Téléchargez et exécutez le programme d’installation pour cette version. Le programme d’installation détecte l’instance existante, ajoute une option de liaison et retourne une liste d’instances compatibles.
+ Choisissez l’instance que vous souhaitez lier, puis sur Terminer le programme d’installation pour exécuter la liaison.

En termes d’expérience utilisateur, la technologie et la façon dont vous travaillez avec lui est inchangé. La seule différence est la présence de packages de contrôle de version plus récente et éventuellement d’autres packages non initialement disponibles dans SQL Server (par exemple, MicrosoftML pour les clients SQL Server 2016 R Services).

## <a name="bkmk_BindWizard"></a>Lier à MLS à l’aide du programme d’installation

Le programme d’installation de Microsoft Machine Learning détecte les fonctionnalités existantes et la version de SQL Server et appelle un utilitaire appelé SqlBindR.exe pour modifier la liaison. En interne, SqlBindR est chaîné à un programme d’installation et utilisée indirectement. Une version ultérieure, vous pouvez appeler SqlBindR directement à partir de la ligne de commande afin d’exercer des options spécifiques.

1. Dans SSMS, exécutez `SELECT @@version` pour vérifier le serveur répond aux exigences de build minimale. 

   Pour SQL Server 2016 R Services, la valeur minimale est [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) et [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Vérifier la version de base de R et les packages RevoScaleR pour vérifier les versions existantes sont inférieurs à ceux de ce que vous envisagez de les remplacer par. Pour SQL Server 2016 R Services, package de Base de R est 3.2.2 et RevoScaleR est 8.0.3.

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

1. Fermez SSMS et n’importe quel outil ayant une connexion ouverte à SQL Server. Liaison remplace les fichiers de programme. Si SQL Server a les sessions ouvertes, la liaison échoue avec le code d’erreur de liaison 6.

1. Télécharger Microsoft Machine Learning Server sur l’ordinateur qui dispose de l’instance que vous souhaitez mettre à niveau. Nous vous recommandons du [version la plus récente](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Décompressez le dossier et démarrer ServerSetup.exe, situé sous MLSWIN93.

   ![Assistant Installation de Microsoft Machine Learning Server](media/mls-921-installer-start.PNG)

1. Sur **configurer l’installation**, vérifiez les composants à mettre à niveau et passez en revue la liste des instances compatibles. 

   Cette étape est très importante.

   Sur la gauche, choisissez toutes les fonctionnalités que vous souhaitez conserver ou de mettre à niveau. Vous ne pouvez pas mettre à niveau certaines fonctionnalités et pas pour d’autres. Une case à cocher vide supprime cette fonctionnalité, en supposant qu’il est actuellement installé. Dans la capture d’écran, une instance donnée de SQL Server 2016 R Services (MSSQL13), R et la version de R des modèles formés préalable sont sélectionnés. Cette configuration est valide, car SQL Server 2016 prend en charge R, mais pas Python.

   Si vous mettez à niveau des composants sur SQL Server 2016 R Services, ne sélectionnez pas la fonctionnalité de Python. Vous ne pouvez pas ajouter Python à SQL Server 2016 R Services.

   Sur la droite, sélectionnez la case à cocher en regard du nom d’instance. Si aucune instance n’est répertorié, vous avez une combinaison incompatible. Si vous ne sélectionnez pas une instance, une nouvelle installation autonome de Machine Learning Server est créée, et les bibliothèques de SQL Server sont identiques. Si vous ne pouvez pas sélectionner une instance, il ne peut pas être à [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Configurer l’étape d’installation](media/mls-931-installer-mssql13.png)

1. Sur le **contrat de licence** page, sélectionnez **J’accepte les termes** pour accepter les termes du contrat de licence pour Machine Learning Server. 

1. Sur des pages successives, donner son consentement à des conditions de licence supplémentaires pour tous les composants open source sélectionné, tel que Microsoft R Open ou de la distribution Anaconda de Python.

1. Sur le **vous y êtes presque** page, notez le dossier d’installation. Le dossier par défaut est \Program Files\Microsoft\ML Server.

    Si vous souhaitez modifier le dossier d’installation, cliquez sur **avancé** pour revenir à la première page de l’Assistant. Toutefois, vous devez répéter toutes les sélections précédentes.

Pendant le processus d’installation, toutes les bibliothèques R ou Python utilisés par SQL Server sont remplacés et Launchpad est mis à jour pour utiliser les composants les plus récents. Par conséquent, si l’instance utilisée précédemment bibliothèques dans le dossier R_SERVICES par défaut, après mise à niveau ces bibliothèques sont supprimées et les propriétés pour le service Launchpad sont modifiées pour utiliser les bibliothèques dans le nouvel emplacement.

Liaison affecte le contenu de ces dossiers : C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library est remplacé par le contenu de C:\Program Files\Microsoft\ML Server\R_SERVER. Le deuxième dossier et son contenu est créé par le programme d’installation de Microsoft Machine Learning Server. 

Si la mise à niveau échoue, vérifiez [codes d’erreur SqlBindR](#sqlbindr-error-codes) pour plus d’informations.

## <a name="confirm-binding"></a>Confirmer la liaison

Revérifier la version de R et RevoScaleR pour confirmer que les versions plus récentes. Utilisez la console R distribuée avec les packages R dans votre instance du moteur de base de données pour obtenir des informations de package :

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

Pour SQL Server 2016 R Services liés à Machine Learning Server 9.3, package de Base de R doit être 3.4.3, RevoScaleR doit être 9.3, et vous devez également avoir MicrosoftML 9.3. 

Si vous avez ajouté les modèles préentraînés, les modèles sont incorporés dans la bibliothèque de MicrosoftML et vous pouvez les appeler via les fonctions de MicrosoftML. Pour plus d’informations, consultez [exemples R pour MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Liaison hors ligne (aucun accès internet)

Pour les systèmes sans connectivité internet, vous pouvez télécharger les fichiers .cab et de programme d’installation sur un ordinateur connecté à internet et puis transférez les fichiers vers le serveur isolé. 

Le programme d’installation (ServerSetup.exe) inclut les packages de Microsoft (RevoScaleR, MicrosoftML, olapR, sqlRUtils). Les fichiers .cab fournissent d’autres composants de base. Par exemple, le fichier cab « SRO » fournit R Open, distribution Microsoft de R. open source

Les instructions suivantes expliquent comment placer les fichiers pour une installation hors connexion.

1. Téléchargez le programme d’installation MLS. Il télécharge dans un fichier compressé unique. Nous vous recommandons du [version la plus récente](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer), mais vous pouvez également installer [les versions antérieures](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components).

1. Téléchargez les fichiers .cab. Les liens suivants concernent la version 9.3. Si vous avez besoin des versions antérieures, vous trouverez des liens supplémentaires dans [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Rappelez-vous que Python/Anaconda peut uniquement être ajouté à une instance de SQL Server 2017 Machine Learning Services. Modèles préentraînés existent pour R et Python ; le fichier .cab fournit des modèles dans les langues que vous utilisez.

    | Fonctionnalité | Télécharger |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Modèles dont l’apprentissage a déjà été effectué | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Transfert de fichiers zip et CAB vers le serveur cible.

1. Sur le serveur, tapez `%temp%` dans la commande Exécuter pour obtenir l’emplacement physique du répertoire temp. Le chemin d’accès physique varie selon l’ordinateur, mais il est généralement `C:\Users\<your-user-name>\AppData\Local\Temp`.

1. Placez les fichiers .cab dans le dossier % Temp%.

1. Décompressez le programme d’installation.

1. Exécutez ServerSetup.exe et suivez les invites à l’écran pour terminer l’installation.

## <a name="bkmk_BindCmd"></a>Opérations de ligne de commande

Une fois que vous exécutez Microsoft Machine Learning Server, un utilitaire de ligne de commande appelé SqlBindR.exe devient disponible que vous pouvez utiliser pour la liaison des opérations. Par exemple, si vous décidez d’inverser une liaison, vous pouvez réexécuter le programme d’installation ou utiliser l’utilitaire de ligne de commande. En outre, vous pouvez utiliser cet outil pour vérifier par exemple compatibilité et la disponibilité.

> [!TIP]
> Impossible de trouver le SqlBindR ? Vous avez exécuté probablement pas le programme d’installation. SqlBindR est disponible uniquement après l’exécution de programme d’installation de Machine Learning Server.

1. Ouvrez une invite de commandes en tant qu’administrateur et accédez au dossier contenant sqlbindr.exe. L’emplacement par défaut est C:\Program Files\Microsoft\MLServer\Setup

2. Tapez la commande suivante pour afficher la liste des instances disponibles : `SqlBindR.exe /list`
  
   Notez le nom complet de l’instance tel qu’il est répertorié. Par exemple, le nom d’instance peut être MSSQL14. MSSQLSERVER pour une instance par défaut, ou quelque chose comme nom du serveur. MYNAMEDINSTANCE.

3. Exécutez le **SqlBindR.exe** commande avec le */lier* argument et spécifiez le nom de l’instance à mettre à niveau, à l’aide du nom d’instance qui a été retourné à l’étape précédente.

   Par exemple, pour mettre à niveau l’instance par défaut, tapez :  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Une fois la mise à niveau terminée, redémarrez le service Launchpad associé à n’importe quelle instance a été modifié.

## <a name="bkmk_Unbind"></a>Rétablir ou annuler la liaison d’une instance

Vous pouvez restaurer une instance liée à une installation initiale des composants R et Python, établie par le programme d’installation de SQL Server. Il existe trois parties pour le retour à la maintenance de SQL Server.

+ [Étape 1 : Annuler la liaison à partir de Microsoft Machine Learning Server](#step-1-unbind)
+ [Étape 2 : Restauration de l’instance de l’état d’origine](#step-2-restore)
+ [Étape 3 : Réinstaller les packages que vous avez ajouté à l’installation](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Étape 1 : Séparer

Vous avez deux options pour annuler la liaison : ré-exécutez de nouveau le programme d’installation ou d’utiliser l’utilitaire de ligne de commande SqlBindR.

#### <a name="bkmk_wizunbind"></a> Annuler la liaison à l’aide du programme d’installation

1. Recherchez le programme d’installation pour Machine Learning Server. Si vous avez supprimé le programme d’installation, vous devrez peut-être télécharger à nouveau, ou copiez-le à partir d’un autre ordinateur.
2. Veillez à exécuter le programme d’installation sur l’ordinateur qui a l’instance que vous souhaitez annuler la liaison.
2. Le programme d’installation identifie les instances locales qui sont candidates pour l’annulation de la liaison.
3. Désélectionnez la case à cocher en regard de l’instance que vous souhaitez revenir à la configuration d’origine.
4. Acceptez le contrat de licence. Vous devez indiquer votre acceptation des termes du contrat de licence même lors de l’installation.
5. Cliquez sur **Terminer**. Le processus prend un certain temps.

#### <a name="bkmk_cmdunbind"></a> Annuler la liaison à l’aide de la ligne de commande

1. Ouvrez une invite de commandes et accédez au dossier qui contient **sqlbindr.exe**, comme décrit dans la section précédente.

2. Exécutez la commande **SqlBindR.exe** avec l’argument */unbind*, puis spécifiez l’instance.

   Par exemple, la commande suivante rétablit l’instance par défaut :
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Étape 2 : Réparez l’instance de SQL Server

Exécutez le programme d’installation de SQL Server pour réparer l’instance du moteur de base de données ayant les fonctionnalités de R et Python. Mises à jour existantes sont conservées, mais si vous avez manqué toute maintenance des mises à jour des packages R et Python de SQL Server, cette étape s’applique les correctifs.

Il s’agit plus de travail, mais vous pouvez également désinstaller complètement et réinstaller l’instance du moteur de base de données, puis appliquer toutes les mises à jour de service.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Étape 3 : Ajouter tous les packages tiers

Vous avez peut-être ajouté des autres packages tiers ou open source à votre bibliothèque de package. Dans la mesure où en inversant la liaison bascule à l’emplacement de la bibliothèque de package par défaut, vous devez réinstaller les packages à la bibliothèque R et Python est maintenant à l’aide. Pour plus d’informations, consultez [par défaut des packages](installing-and-managing-r-packages.md), [installer de nouveaux packages R](install-additional-r-packages-on-sql-server.md), et [installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>Syntaxe de commande SqlBindR.exe

### <a name="usage"></a>Utilisation

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Paramètres

|Créer une vue d’abonnement|Description|
|------|------|
|*list*| Affiche une liste de tous les ID d’instances de bases de données SQL sur l’ordinateur actuel|
|*bind*| Met à niveau l’instance de base de données SQL spécifiée vers la version la plus récente de R Server, et garantit que l’instance obtient automatiquement les mises à niveau ultérieures de R Server|
|*unbind*|Désinstalle la version la plus récente de R Server de l’instance de base de données SQL spécifiée, et empêche les mises à niveau ultérieures de R Server d’affecter l’instance|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Erreurs de liaison

Programme d’installation MLS et SqlBindR retournent les codes d’erreur suivants et les messages.

|Code d'erreur  | Message           | Détails               |
|------------|-------------------|-----------------------|
|Lier l’erreur 0 | OK (réussite) | Liaison transmis sans erreur. |
|Lier l’erreur 1 | Arguments non valides | Erreur de syntaxe. |
|Erreur 2 de liaison | Action non valide | Erreur de syntaxe. |
|Lier l’erreur 3 | Instance non valide | Une instance existe, mais n’est pas valide pour la liaison. |
|Lier l’erreur 4 | Ne peut pas être liée | |
|Lier l’erreur 5 | Déjà liée | Vous avez exécuté la commande *bind* , mais l’instance spécifiée est déjà liée. |
|Lier l’erreur 6 | Échec de la liaison | Une erreur s’est produite lors de la séparation de l’instance. Cette erreur peut se produire si vous exécutez le programme d’installation MLS sans sélectionner toutes les fonctionnalités. Liaison requiert que vous sélectionnez une instance MSSQL et R et Python, en supposant que l’instance est SQL Server 2017. Cette erreur se produit également si SqlBindR ne peut pas écrire dans le dossier Program Files. Sessions ouvertes ou des handles vers SQL Server provoque cette erreur se produise. Si vous obtenez cette erreur, redémarrez l’ordinateur et répéter les étapes de la liaison avant de commencer les nouvelles sessions.|
|Liaison d’erreur 7 | Non lié | L’instance du moteur de base de données a R Services ou SQL Server Machine Learning Services. L’instance n’est pas lié à Microsoft Machine Learning Server. |
|Lier l’erreur 8 | Annuler la liaison a échoué | Une erreur s’est produite lors de la séparation de l’instance. |
|Lier l’erreur 9 | Aucune instance trouvée | Aucune instance de moteur de base de données ont été trouvés sur cet ordinateur. |

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie des problèmes connus spécifiques à l’aide de l’utilitaire SqlBindR.exe ou aux mises à niveau de Machine Learning Server susceptibles d’affecter les instances de SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Restauration des packages qui ont été installés précédemment

Si vous mettez à niveau Microsoft R Server 9.0.1, la version de SqlBindR.exe pour cette version Impossible de restaurer les packages d’origine ou des composants R complètement, demandant à l’utilisateur d’exécuter la réparation de SQL Server sur l’instance, s’appliquent à toutes les versions de service, puis redémarrez l’instance.

Une version ultérieure de SqlBindR automatiquement restaurer les fonctionnalités de R d’origine, en éliminant la nécessité de réinstallation des composants R ou ré-appliquer le correctif. Toutefois, vous devez installer les mises à jour de package R qui ont peuvent être ajoutés après l’installation initiale.

Si vous avez utilisé les rôles de gestion de package pour installer et partager le package, cette tâche est beaucoup plus facile : vous pouvez utiliser des commandes R pour synchroniser des packages installés dans le système de fichiers à l’aide d’enregistrements dans la base de données et vice versa. Pour plus d’informations, consultez [gestion des packages R pour SQL Server](install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Problèmes liés à plusieurs mises à niveau à partir de SQL Server

Si vous avez précédemment mis à niveau une instance de SQL Server 2016 R Services vers 9.0.1, lorsque vous exécutez le nouveau programme d’installation de Microsoft R Server 9.1.0)., il affiche une liste de toutes les instances valides, puis sélectionne précédemment liée d’instances par défaut. Si vous continuez, les instances précédemment liés sont indépendants. Par conséquent, la 9.0.1 antérieures installation est supprimée, y compris tous les packages, mais la nouvelle version de Microsoft R Server (9.1.0).) n’est pas installée.

Pour résoudre ce problème, vous pouvez modifier l’installation de R Server existante comme suit :
1. Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.
2. Recherchez Microsoft R Server, puis cliquez sur **changer/modifier**.
3. Lorsque le programme d’installation démarre, sélectionnez les instances que vous souhaitez lier à 9.1.0).

Microsoft Machine Learning Server 9.2.1 et 9.3 n’ont pas ce problème.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>La liaison ou de dissociation laisse plusieurs dossiers temporaires

La liaison et annulation de la liaison des opérations échouent parfois nettoyer les dossiers temporaires.
Si vous trouvez des dossiers avec un nom tel que cela, vous pouvez le supprimer une fois l’installation terminée : R_SERVICES_<guid>

> [!NOTE]
> Veillez à attendre jusqu'à ce que l’installation est terminée. Il peut prendre beaucoup de temps à supprimer les bibliothèques R associé liés une version, puis ajoutez les nouvelles bibliothèques R. Lorsque l’opération est terminée, les dossiers temporaires sont supprimés.

## <a name="see-also"></a>Voir aussi

+ [Installer Machine Learning Server pour Windows (connecté à Internet)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installer Machine Learning Server pour Windows (hors connexion)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Problèmes connus dans Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Annonces de fonctionnalités à partir de la version précédente de R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Fonctionnalités déconseillées, supprimées ou modifiées](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
