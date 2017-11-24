---
title: "Installation des composants d’apprentissage machine sans accès à internet | Documents Microsoft"
ms.custom: 
ms.date: 11/30/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "30"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 065f66ca4d1e94e021b1d65b379c4a79302b1066
ms.sourcegitcommit: ec5f7a945b9fff390422d5c4c138ca82194c3a3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="installing-machine-learning-components-without-internet-access"></a>Installation des composants d’apprentissage machine sans accès à internet

Étant donné que les composants R et Python fournis avec SQL Server 2016 et SQL Server 2017 sont open source, Microsoft n’installe pas les composants de R ou Python par défaut. Au lieu de cela, nous fournir les programmes d’installation connexes et fourni des packages pour des raisons pratiques du Microsoft Download Center et d’autres sites de confiance. Vous devez donner son consentement à la licence appropriée, et ensuite le programme d’installation de SQL Server installe les composants de R ou Python pour vous.

Cette rubrique fournit les emplacements de téléchargement pour les programmes d’installation et une vue d’ensemble du processus d’installation hors connexion.

## <a name="overview-of-the-offline-installation-process"></a>Vue d’ensemble du processus d’installation hors connexion

En règle générale, le programme d’installation des composants d’ordinateur utilisé dans SQL Server 2016 et SQL Server 2017 nécessite une connexion internet. Lorsque le programme d’installation de SQL Server s’exécute, si vous avez sélectionné une des options d’apprentissage, le programme d’installation vérifie les Python ou R programmes d’installation, ainsi que toutes les autres composants requis.

+ **Si l’ordinateur possède une connexion internet**

    SQL Server localise et télécharge les composants pour vous et les installe ensuite pendant l’installation. Accepter les termes du contrat de licence séparément pour chaque composant open source (R ou Python) que vous installez.

+ **Si l’ordinateur n’a pas accès à internet**

    Vous devez télécharger les programmes d’installation supplémentaires avant de poursuivre l’installation. Au minimum, téléchargez les programmes d’installation R ou Python qui sont pris en charge pour la version de SQL Server que vous installez.

    Selon la configuration de votre serveur, vous devrez peut-être des composants supplémentaires.  Consultez [des composants supplémentaires](#bkmk_OtherComponents) pour plus d’informations.

    Une fois que vous avez téléchargé les programmes d’installation, utilisez-les lors de l’installation de la fonctionnalité dans le cadre du programme d’installation de SQL Server.

### <a name="step-1-obtain-additional-installers"></a>Étape 1. Obtenir des programmes d’installation supplémentaires

**Pour R**

Le langage R est pris en charge dans SQL Server 2016 et SQL Server 2017. Deux programmes d’installation différentes sont nécessaires, pour ouvrir la source et des composants propriétaires. L’Assistant Installation de SQL Server permet de s’assurer qu’elles sont installées dans le bon ordre.

+ Programmes d’installation avec **SRO** dans le nom de fournir les composants open source.
+ Programmes d’installation avec **SRS** dans le nom contient des composants fournis par Microsoft, y compris celles pour l’intégration de base de données.

**Pour Python**

Le langage Python est pris en charge uniquement dans SQL Server 2017. Il existe encore des deux programmes d’installation distincts que vous devez télécharger.

+ Programmes d’installation avec **simulé** dans le nom de Microsoft Open de Python et fournissent les composants d’ouvrir la source.
+ Programmes d’installation avec **SPS** dans le nom sont pour Microsoft Server de Python et contiennent des composants fournis par Microsoft, y compris celles pour l’intégration de base de données.

**Le téléchargement**

1. Télécharger les programmes d’installation à partir de la [sites Microsoft Download Center](#installerlocs) sur un ordinateur connecté à internet et d’enregistrer le programme d’installation, plutôt que de son exécution.
2. Copiez les fichiers du programme d’installation (CAB) sur l’ordinateur où vous prévoyez d’installer les composants de la machine learning.
3. Dans SQL Server 2016, l’Assistant Installation installé anglais par défaut. Pour installer à l’aide d’une autre langue requis modification du nom de fichier du programme d’installation, comme décrit ici : [Modifications requises pour les paramètres régionaux de langue différents](#modslocales).
    Pour SQL Server 2017, la langue correcte est identifiée selon les paramètres régionaux d’instance.
4. Télécharger tous les composants supplémentaires sont requises, telles que MPI ou .NET Core.
5. Si vous le souhaitez, vous pouvez télécharger le code source archivé pour les composants open source, mais cela n’est pas requis pour le programme d’installation de SQL Server et peut être effectuée à tout moment. Pour plus d’informations, consultez [R Server pour Windows](https://docs.microsoft.com/r-server/install/r-server-install-windows).

Pour une procédure pas à pas du processus d’installation hors connexion pour R Services dans SQL Server 2016, nous vous recommandons de l’article par le [SQL Server Customer Advisory Team](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/). l’article inclut des captures d’écran et couvre également les scénarios d’installation intégrée et de mise à jour corrective.

### <a name="step-2-run-offline-setup-using-the-sql-server-setup-wizard"></a>Étape 2. Exécutez le programme d’installation hors connexion à l’aide de l’Assistant Installation de SQL Server

1. Ouvrez l’Assistant Installation de SQL Server.
2. Lorsque l’Assistant Installation affiche la page de gestion des licences, cliquez sur **accepter**.
3. Ouvre de boîte de dialogue qui vous invite à entrer le **chemin d’installation** des packages requis.
4. Cliquez sur **Parcourir** pour localiser le dossier contenant les fichiers de programme d’installation que vous avez copiée précédemment.
5. Si les fichiers appropriés sont présents, vous pouvez cliquer sur **Suivant** pour indiquer que les composants sont disponibles.
10. Effectuez le reste des étapes de l’Assistant Installation de SQL Server.
11. Effectuez les étapes de post-installation requises pour vous assurer que le service est activé.

## <a name="installerlocs"></a>Emplacement de téléchargement de composants de machine learning

> [!NOTE]
> Veillez à obtenir les fichiers qui correspondent à la version de SQL Server, vous installez.
> 
> Prise en charge de Python est fourni avec SQL Server 2017 CTP 2.0. Les versions antérieures, y compris SQL Server 2016, ne prennent pas en charge Python.

+ [Pour obtenir des composants R pour SQL Server 2016](#bkmk_2016Installers)

+ [Pour obtenir des composants R ou Python pour SQL Server 2017](#bkmk_2017Installers)

### <a name="bkmk_2017Installers"></a>Téléchargements pour SQL Server 2017

Version  |Télécharger le lien  |
---------|---------|
**SQL Server 2017 CTP 1**     |
Microsoft R Open     |[SRO_3.3.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_9.0.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server CTP 2017 1.1** |
Microsoft R Open     |[SRO_3.3.2.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834568)
Microsoft R Server     |[SRS_9.0.1.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834567)
**SQL Server 2017 CTP 1.4** |
Microsoft R Open     |[SRO_3.3.2.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842483)
Microsoft R Server     |[SRS_9.0.2.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842482)
**SQL Server 2017 CTP 2.0** |
Microsoft R Open     |[SRO_3.3.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842800)
Microsoft R Server     |[SRS_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842799)
Python de Microsoft Open     |[SPO_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842828)
Python de Microsoft Server    |[SPS_9.1.0.0__1033.cab](https://go.microsoft.com/fwlink/?LinkId=842848)
**SQL Server 2017 RC1** |
Microsoft R Open     |[SRO_3.3.3.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851503)|
Microsoft R Server     |[SRS_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851498)|
Python de Microsoft Open     |[SPO_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851499)|
Python de Microsoft Server    |[SPS_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851504)|
**SQL Server 2017 RC 2** |
Microsoft R Open     |[SRO_3.3.3.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851493)|
Microsoft R Server     |[SRS_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851505)|
Python de Microsoft Open     |[SPO_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851506)|
Python de Microsoft Server    |[SPS_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851497)|
**SQL Server 2017 RTM** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Python de Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Python de Microsoft Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |
**SQL Server 2017 CU1** |
Microsoft R Open     |utiliser le précédent|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Python de Microsoft Open     |utiliser le précédent |
Python de Microsoft Server    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**SQL Server 2017 CU2** |
Microsoft R Open     |utiliser le précédent|
Microsoft R Server      |utiliser le précédent|
Python de Microsoft Open     |utiliser le précédent |
Python de Microsoft Server    |utiliser le précédent|

### <a name="bkmk_2016Installers"></a>Téléchargements pour SQL Server 2016

> [!IMPORTANT]
> 
> Lors de l’installation de SQL Server 2016 SP1 CU4 ou SP1 CU5 hors connexion, téléchargez SRO_3.2.2.16000_1033.cab. Si vous avez téléchargé SRO_3.2.2.13000_1033.cab FWLINK 831785 comme indiqué dans la boîte de dialogue d’installation, renommez le fichier en tant que SRO_3.2.2.16000_1033.cab avant d’installer la mise à jour Cumulative.

Version  |Télécharger le lien  |
---------|---------|
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)
**SQL Server 2016 CU 1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 CU 2**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 CU 3**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server     | aucune modification ; utiliser le précédent |
**SQL Server 2016 CU 4**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU 5**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server     |aucune modification ; utiliser le précédent|
**SQL Server 2016 CU 6**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server     |[SRS_8.0.3.14000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850316)  |
**SQL Server 2016 CU 7**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server     |aucune modification ; utiliser le précédent |
**SQL Server 2016 SP 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 SP 1 CU1**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server     |aucune modification ; utiliser le précédent|
**SQL Server 2016 SP1 CU2**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP 1 CU3**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server     |aucune modification ; utiliser le précédent|
**GDR et SQL Server 2016 SP 1 CU4**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP 1 CU5**     |
Microsoft R Open     |aucune modification ; utiliser le précédent|
Microsoft R Server    |aucune modification ; utiliser le précédent |

Si vous souhaitez afficher le code source pour Microsoft R, il est disponible en téléchargement sous forme d’archive .tar format : [programmes d’installation de télécharger le serveur R](https://docs.microsoft.com/r-server/install/r-server-install-windows#download)

### <a name = "bkmk_OtherComponents"></a>Autres conditions préalables

Selon votre environnement, vous devrez peut-être effectuer des copies locales des programmes d’installation pour les prérequis suivants.

Composant  |Version
---------|---------
[Fournisseur Microsoft OLE DB AS pour SQL Server 2016](https://go.microsoft.com/fwlink/?linkid=834405)     |  13.0.1601.5
[Microsoft .NET Core](https://go.microsoft.com/fwlink/?linkid=834319)     | 1.0.1
[Microsoft MPI](https://go.microsoft.com/fwlink/?linkid=834316)     | 7.1.12437.25
[Microsoft Visual C++ 2013 Redistributable](https://go.microsoft.com/fwlink/?linkid=799853)     | 12.0.30501.0
[Microsoft Visual C++ 2015 Redistributable](https://go.microsoft.com/fwlink/?linkid=828641)     | 14.0.23026.0

## <a name="modslocales"></a>L’installation pour les paramètres régionaux de langue différente

Si vous téléchargez la. Fichiers CAB dans le cadre du programme d’installation de SQL Server sur un ordinateur connecté à internet, l’Assistant installation détecte la langue locale et modifie automatiquement la langue de l’installer.

Toutefois, selon votre version de SQL Server, vous devrez peut-être effectuer des étapes supplémentaires pour installer les composants R localisés sur un ordinateur sans accès à internet.

+ **Pour SQL Server 2016**

   Après avoir téléchargé les programmes d’installation de R sur un partage local, vous devrez peut-être modifier manuellement le nom des fichiers téléchargés pour insérer l’identificateur de langue approprié pour la langue que vous installez.

    Par exemple, pour installer la version japonaise de SQL Server, vous modifierait le nom du fichier à partir de SRS_8.0.3.0_**1033**.cab à SRS_8.0.3.0_**1041**.cab.

    > [!IMPORTANT]
    > Ce problème s’applique uniquement aux premières versions et a été résolu dans les versions ultérieures.
    > **Utilisez uniquement cette solution de contournement si le programme d’installation renvoie un message qu’il ne peut pas installer la langue appropriée.**

+ **Pour SQL Server 2017**

    Téléchargez la. Fichier CAB pour les composants de R ou Python.
    
    La langue est détectée selon les paramètres régionaux du serveur. Les paramètres régionaux corrects sont automatiquement installé à l’aide de téléchargé. Fichier CAB.

## <a name="slipstream-upgrades"></a>Mises à niveau de l’installation intégrée

Une installation intégrée renvoie à la possibilité d’appliquer un correctif ou une mise à jour à une installation d’instance défaillante dans le but de corriger les problèmes existants. L’avantage de cette méthode est que SQL Server est mis à jour en même temps que vous effectuez l’installation, ce qui évite d’avoir à effectuer par la suite un redémarrage séparé.

+ Si le serveur n’a pas accès à Internet, vous devez télécharger le programme d’installation de SQL Server, puis télécharger les versions correspondantes des programmes d’installation des composants R **avant** de commencer le processus de mise à jour.  Les composants R ne sont pas inclus par défaut avec SQL Server.

+ Si vous êtes *ajout* ces composants d’un *existant* installation, utilisez la version mise à jour du programme d’installation de SQL Server, correspondants de mise à jour la version des composants supplémentaires. Lorsque vous spécifiez que la fonctionnalité de R doit être installé, le programme d’installation recherche la version correspondante des programmes d’installation pour les composants d’apprentissage automatique.

## <a name="command-line-arguments-for-specifying-component-locations"></a>Arguments de ligne de commande pour spécifier les emplacements des composants

Lorsque vous effectuez une installation en mode hors connexion à partir de la ligne de commande, vous devez fournir les arguments de ligne de commande suivants pour spécifier l’emplacement des composants que vous avez téléchargé à l’avance. Toutefois, vous n’avez pas besoin de définir tous les indicateurs supplémentaires pour installer les composants requis supplémentaires ; conditions préalables telles que .NET core sont installés en mode silencieux par défaut.

**Emplacement de programmes d’installation**

- `/UPDATESOURCE`Pour spécifier l’emplacement du fichier local contenant le programme d’installation de la mise à jour de SQL Server
- `/MRCACHEDIRECTORY`Pour spécifier le dossier contenant les fichiers CAB des composants R
- `/MPYCACHEDIRECTORY`Pour spécifier le dossier contenant les fichiers CAB du composant Python

**Composants de R dans SQL Server 2016**

- `/ADVANCEDANALYTICS`Pour obtenir un support technique du moteur de scripts externes
- `/IACCEPTROPENLICENSETERMS="True"`pour accepter R distinct contrat de licence

**Composants de R dans SQL Server 2017**

- `/ADVANCEDANALYTICS`Pour obtenir un support technique du moteur de scripts externes
- `/SQL_INST_MR`Pour utiliser R
- `/IACCEPTROPENLICENSETERMS="True"`pour accepter R distinct contrat de licence

**Composants de Python dans SQL Server 2017**

- `/ADVANCEDANALYTICS`Pour obtenir un support technique du moteur de scripts externes
- `/SQL_INST_MPY`Pour utiliser Python
- `/IACCEPTPYTHONLICENSETERMS="True"`pour accepter les Python distinct contrat de licence


> [!NOTE]
> Vous ne pouvez pas modifier le compte de service pour Launchpad, à l’aide des paramètres dans le programme d’installation de SQL Server. Nous recommandons que vous installez à l’aide de comptes de service par défaut et modifiez le compte de service à l’aide du Gestionnaire de Configuration SQL Server. Après cela, veillez à redémarrer le service Launchpad.

## <a name="see-also"></a>Voir aussi

[Installer Microsoft R Server](https://docs.microsoft.com/r-server/install/r-server-install-windows)

Cet article par l’équipe de prise en charge des Services R montre comment effectuer une installation sans assistance ou une mise à niveau de R services dans SQL Server 2016 : [déploiement R Services sur des ordinateurs sans accès à Internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).
