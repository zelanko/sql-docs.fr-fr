---
title: "L’installation des composants sans accès à Internet d’apprentissage | Documents Microsoft"
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 30
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7307104b9ad5df2bb8f034525cc82847d21a14bf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="installing-machine-learning-components-without-internet-access"></a>L’installation des composants sans accès à Internet d’apprentissage

Étant donné que les composants R et Python fournis avec SQL Server 2016 ou SQL Server 2017 sont open source, Microsoft n’installe pas les composants de R ou Python par défaut.

Au lieu de cela, nous fournir les programmes d’installation connexes et fourni des packages pour des raisons pratiques du Microsoft Download Center et d’autres sites de confiance. Vous devez donner son consentement à la licence appropriée, et ensuite le programme d’installation de SQL Server installera les composants R ou Python pour vous.

Cette rubrique fournit les emplacements de téléchargement pour les programmes d’installation et une vue d’ensemble du processus d’installation hors connexion.

## <a name="installation-process"></a>Processus d'installation

En règle générale, le programme d’installation des composants d’ordinateur utilisé dans SQL Server 2016 et SQL Server 2017 nécessite une connexion Internet. Lorsque le programme d’installation de SQL Server s’exécute, si vous avez sélectionné les options learnig machine, le programme d’installation recherche les Python ou R programmes d’installation, ainsi que toutes les autres composants requis. S’il existe une connexion Internet, SQL Server les installer pour vous.

> [!IMPORTANT]
> Sur un serveur sans accès à Internet, vous devez télécharger les programmes d’installation supplémentaires avant de poursuivre l’installation.

Au minimum, vous devez télécharger les programmes d’installation R ou Python qui sont pris en charge pour la version ou numéro de build de SQL Server que vous installez.

Selon la configuration de votre serveur, vous devrez peut-être des composants supplémentaires, tels que .NET Core.  Consultez [des composants supplémentaires](#bkmk_OtherComponents) pour plus d’informations.

Une fois que vous avez téléchargé les programmes d’installation, utilisez-les lors de l’installation de la fonctionnalité dans le cadre du programme d’installation de SQL Server.

### <a name="step-1-obtain-additional-installers"></a>Étape 1. Obtenir des programmes d’installation supplémentaires

Pour **R** dans SQL Server 2016 et SQL Server 2017, vous devez obtenir deux programmes d’installation différents. L’Assistant de configuration de SQL Server garantit qu’ils sont installés dans le bon ordre.

+ Programmes d’installation avec **SRO** dans le nom de fournir les composants open source.
+ Insallers avec **SRS** dans le nom contient des composants fournis par Microsoft, y compris celles pour l’intégration de base de données.


Pour **Python** dans SQL Server 2017, téléchargez le fichier CAB et tous les éléments requis.


1. Sur un ordinateur connecté à Internet, téléchargez les programmes d’installation à partir du [Centre de téléchargement Microsoft](#installerlocs), puis choisissez de les enregistrer plutôt que de les exécuter.
2. Copiez les fichiers du programme d’installation (CAB) sur l’ordinateur où vous allez installer les composants de la machine learning.
3. Actuellement, l’Assistant Installation installe anglais par défaut. Pour installer à l’aide d’une langue différente, modifiez les noms de fichiers du programme d’installation comme décrit ici : [Modifications nécessaires pour différents paramètres régionaux de langue](#modslocales).
4. Télécharger tous les composants supplémentaires sont requises, telles que MPI ou .NET Core.
5. Si vous le souhaitez, vous pouvez télécharger le code source archivé pour les composants open source, mais cela n’est pas requis pour le programme d’installation de SQL Server et peut être effectuée à tout moment. Pour plus d’informations, consultez [R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows).


> [!NOTE]
> Veillez à ce que les fichiers correspondent à la version de SQL Server que vous allez installer.
> 
> Prise en charge de Python est fourni dans SQL Server 2017 CTP 2.0. Les versions antérieures, y compris SQL Server 2016, ne prennent pas en charge Python.

Pour une procédure pas à pas du processus d’installation hors connexion pour R Services dans SQL Server 2016, nous vous recommandons de l’article par le [SQL Server Customer Advisory Team](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/). Cet article aborde également les scénarios de mise à jour corrective et d’installation intégrée.


### <a name="step-2-run-offline-setup-using-the-sql-server-setup-wizard"></a>Étape 2. Exécutez le programme d’installation hors connexion à l’aide de l’Assistant Installation de SQL Server

1. Ouvrez l’Assistant Installation de SQL Server.
2. Lorsque l’Assistant Installation affiche la page de gestion des licences, cliquez sur **accepter**.
3. Ouvre de boîte de dialogue qui vous invite à entrer le **chemin d’installation** des packages requis.
4. Cliquez sur **Parcourir** pour localiser le dossier contenant les fichiers de programme d’installation que vous avez copiée précédemment.
5. Si les fichiers appropriés sont présents, vous pouvez cliquer sur **Suivant** pour indiquer que les composants sont disponibles.
10. Effectuez le reste des étapes de l’Assistant Installation de SQL Server.
11. Effectuez les étapes de post-installation requises pour vous assurer que le service est activé.

## <a name="installerlocs"></a>Téléchargements

Version  |Télécharger le lien  
---------|---------
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
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)  |
**SQL Server 2016 SP 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 SP 1 GDR**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server 2017 CTP 1**     |
Microsoft R Open     |[SRO_3.3.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_9.0.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server CTP 2017 1.1** |
Microsoft R Open     |[SRO_3.3.2.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834568)
Microsoft R Server     |[SRS_9.0.1.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834567)
**SQL Server 2017 CTP 1.4** |
Microsoft R Open     |[SRO_xxxx_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842483)
Microsoft R Server     |[SRS_xxx.xxx_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842482)
**SQL Server 2017 CTP 2.0** |
Microsoft R Open     |[SRO_3.3.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842800)
Microsoft R Server     |[SRS_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842799)
Python de Microsoft Open     |[SPO_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842828)
Python de Microsoft Server    |[SPS_9.1.0.0__1033.cab](https://go.microsoft.com/fwlink/?LinkId=842848)

Si vous souhaitez afficher le code source pour Microsoft R, il est disponible en téléchargement sous forme d’archive .tar format : [programmes d’installation de télécharger le serveur R](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#download)

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

Si vous téléchargez les fichiers .cab dans le cadre de la configuration de SQL Server sur un ordinateur connecté à Internet, l’Assistant de configuration détecte la langue locale et change automatiquement la langue du programme d’installation.

Toutefois, si vous installez l’une des versions localisées de SQL Server sur un ordinateur sans accès à Internet et téléchargez les programmes d’installation de R vers un partage local, vous devez modifier manuellement le nom des fichiers téléchargés et insérer l’identificateur de langue approprié pour la langue que vous installez.

Par exemple, si vous installez la version japonaise de SQL Server, remplacez le nom du fichier SRS_8.0.3.0_**1033**.cab par SRS_8.0.3.0_**1041**.cab.


## <a name="slipstream-upgrades"></a>Mises à niveau de l’installation intégrée

Une installation intégrée renvoie à la possibilité d’appliquer un correctif ou une mise à jour à une installation d’instance défaillante dans le but de corriger les problèmes existants. L’avantage de cette méthode est que SQL Server est mis à jour en même temps que vous effectuez l’installation, ce qui évite d’avoir à effectuer par la suite un redémarrage séparé.

+ Si le serveur n’a pas accès à Internet, vous devez télécharger le programme d’installation de SQL Server, puis télécharger les versions correspondantes des programmes d’installation des composants R **avant** de commencer le processus de mise à jour.  Les composants R ne sont pas inclus par défaut avec SQL Server.

+ Si vous êtes *ajout* ces composants d’un *existant* installation, utilisez la version mise à jour du programme d’installation de SQL Server, correspondants de mise à jour la version des composants supplémentaires. Lorsque vous spécifiez que la fonctionnalité de R doit être installé, le programme d’installation recherche la version correspondante des programmes d’installation pour les composants d’apprentissage automatique.

## <a name="command-line-arguments-for-setup"></a>Arguments de ligne de commande pour le programme d’installation

Lorsque vous effectuez une installation sans assistance, vous devrez fournir les arguments de ligne de commande suivants. Notez que vous n’avez pas besoin de définir tous les indicateurs supplémentaires pour installer des composants requis. Conditions préalables telles que .NET core sont installés en mode silencieux par défaut.

**Emplacement de programmes d’installation**

- `/UPDATESOURCE`Pour spécifier l’emplacement du fichier local contenant le programme d’installation de la mise à jour de SQL Server
- `/MRCACHEDIRECTORY`Pour spécifier le dossier contenant les fichiers CAB des composants R

**Composants de R dans SQL Server 2016**

- `/ADVANCEDANALYTICS`Pour obtenir un support technique du moteur de scripts externes
- `/IACCEPTROPENLICENSETERMS="True"`pour accepter R distinct contrat de licence

**Composants de R dans SQL Server SQL Server 2017**

- `/ADVANCEDANALYTICS`Pour obtenir un support technique du moteur de scripts externes
- `/SQL_INST_MR`Pour utiliser R
- `/IACCEPTROPENLICENSETERMS="True"`pour accepter R distinct contrat de licence

**Composants de Python dans SQL Server 2017**

- `/ADVANCEDANALYTICS`Pour obtenir un support technique du moteur de scripts externes
- `/SQL_INST_MPY`Pour utiliser Python
- `/IACCEPTPYTHONLICENSETERMS="True"`pour accepter R distinct contrat de licence

> [!TIP]
> Cet article par l’équipe de prise en charge des Services R montre comment effectuer une installation sans assistance ou une mise à niveau de R services dans SQL Server 2016 : [déploiement R Services sur des ordinateurs sans accès à Internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).

## <a name="see-also"></a>Voir aussi

[Installer Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)


