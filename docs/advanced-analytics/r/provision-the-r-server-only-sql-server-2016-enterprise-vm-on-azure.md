---
title: "Configurer un ordinateur virtuel pour l’apprentissage sur Azure | Documents Microsoft"
ms.custom: 
ms.date: 10/16/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8cc1fcfdeae8742a93916dfb08c9db1215f88721
ms.openlocfilehash: 7cb9e069fc3b537f8aab9d048a152435ad0cc6ac
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Configurer un ordinateur virtuel pour l’apprentissage sur Azure

Machines virtuelles sur Azure sont une option pratique pour la configuration rapidement d’un environnement de serveur complet pour les solutions d’apprentissage. Cet article répertorie certaines images de machine virtuelle qui contiennent des R Server, le serveur d’apprentissage Machine ou SQL Server avec un apprentissage.

Cette liste n’est pas destinée à être complète, mais uniquement de fournir les noms des images qui sont liées à Machine Learning Server ou SQL Server Machine Learning Services, pour faciliter la découverte.

> [!TIP]
> Nous vous recommandons d’utiliser la nouvelle version du portail Azure et Azure Marketplace. Certaines images ne sont pas disponibles lorsque vous parcourez la galerie Azure sur le portail classique.

## <a name="how-to-provision-a-virtual-machine"></a>Comment configurer un ordinateur virtuel

Si vous ne connaissez pas à l’aide de machines virtuelles Azure, nous recommandons que vous consultez les articles suivants pour plus d’informations sur l’utilisation du portail et de configurer une machine virtuelle.

+ [Prise en main des machines virtuelles](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Prise en main des Machines virtuelles Windows](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

## <a name="find-a-machine-learning-image"></a>Rechercher une image d’apprentissage machine

1. À partir du portail Azure (portal.azure.com), cliquez sur **virtuels**, ou cliquez sur **nouveau**.

2. Localisez la zone de recherche en haut de la page, vous pouvez utiliser pour filtrer les ressources par nom. 

3. Tapez « Serveur R » (ou « Serveur ML ») dans le **filtre** contrôle pour afficher la liste de ressources liées. Cliquez sur **recherche dans Marketplace** pour afficher les ordinateurs virtuels.

    > [!TIP]
    > 
    > Autres chaînes possibles pour le contrôle de filtre sont « science des données » et « apprentissage ».
    > 
    > Utilisez le `%` génériques dans la recherche pour trouver les noms d’ordinateurs virtuels. Par exemple, vous pouvez taper `"`Julia %` or `%R % ».

4. Pour obtenir les R Server pour Windows, sélectionnez **R Server uniquement SQL Server 2016 Enterprise**.
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) est concédé sous licence en tant qu’une fonctionnalité de SQL Server Enterprise Edition, mais la version 9.1 est installée comme serveur autonome et traitée sous la stratégie de prise en charge du cycle de vie moderne.

    > [!NOTE] 
    > 
    > Cela se situent, recherchez pour la version d’un nouvel ordinateur virtuel qui inclut SQL Server 2017 et le 9.2.1 version du serveur de Machine Learning.
    > En attendant, vous pouvez mettre à jour la version de SQL Server installée sur cet ordinateur virtuel à l’aide du centre d’Installation SQL Server et de l’option de mise à niveau. Pour plus d’informations, consultez [mise à niveau de SQL Server à l’aide de l’Assistant installation](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup).

5. Une fois l’ordinateur virtuel a été créé et est en cours d’exécution, cliquez sur le **Connect** bouton pour ouvrir une connexion et de se connecter au nouvel ordinateur.

5. Une fois que vous vous connectez, vous pouvez installer le package R supplémentaires ou votre outil de développement par défaut.

### <a name="install-additional-r-tools"></a>Installer les outils R supplémentaires

Par défaut, Microsoft R Server inclut tous les outils R installés avec une installation basique de R, notamment RTerm et RGui. Un raccourci vers RGui a également été ajouté sur le bureau.

Toutefois, vous avez tout intérêt à installer les outils R supplémentaires, tels que RStudio, R Tools pour Visual Studio (RTV) ou Microsoft R Client. Consultez les liens suivants pour les emplacements et instructions de téléchargement :

+ [Outils R pour Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio pour Windows](https://www.rstudio.com/products/rstudio/download/)

Une fois l’installation terminée, veillez à changer l’emplacement du runtime R par défaut pour que tous les outils de développement R utilisent les bibliothèques Microsoft R Server.

### <a name="configure-r-server-to-support-web-services"></a>Configurer R Server pour prendre en charge des services web

Une configuration supplémentaire est nécessaire pour déployer le service web, l’exécution à distance, ou pour tirer parti de R Server comme un serveur de déploiement de votre organisation. Pour obtenir des instructions, consultez [configuration du serveur pour opérationnaliser analytique R](https://docs.microsoft.com/machine-learning-server/install/operationalize-r-server-one-box-config).

> [!NOTE]
> Une configuration supplémentaire n’est pas nécessaire si vous souhaitez simplement utiliser les packages tels que RevoScaleR ou MicrosoftML.

## <a name="other-virtual-machines"></a>Autres machines virtuelles

Les images suivantes sont disponibles à partir d’Azure Marketplace et sont entièrement configurés outils d’apprentissage de l’ordinateur, mais n’incluent pas nécessairement de SQL Server.

### <a name="data-science-virtual-machine"></a>Machine virtuelle de science des données

Cette image est préconfigurée avec Microsoft R Server, ainsi que Python (distribution Anaconda), un serveur jupyter Notebook, Visual Studio Community Edition, Power BI Desktop, le Kit de développement logiciel Azure et SQL Server Express edition.

La version de Windows s’exécute sur Windows Server 2012 et contient de nombreux outils spéciaux pour la modélisation et analytique, y compris [CNTK](https://www.microsoft.com/cognitive-toolkit/), [mxNet](https://mxnet.incubator.apache.org/), et des packages R populaire, tel que **xgboost**.

Les versions de Linux sont fournies pour Ubuntu, Centos et Centos CSP et contiennent de nombreux outils courants pour les activités de développement et de la science des données.

Pour plus d’informations, consultez [Introduction à l’ordinateur virtuel Science Azure données pour Linux et Windows](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-vm).

Cette image a été récemment mis à jour pour inclure : 

+ Prise en charge de Julia, la langue de la science des données puissante, évolutive et de demain 
+ JupyterHub, qui est une option utile lorsque vous voulez exécuter une classe de formation et que tous les étudiants pour partager le même serveur, mais utilisez des blocs-notes et des répertoires.

Pour plus d’informations sur les outils pris en charge et des infrastructures de machine learning, consultez [votre Machine virtuelle de science des données de découverte](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-tools-overview)

### <a name="r-server-virtual-machines"></a>Machines virtuelles R Server

Outre la **R Server uniquement SQL Server 2016 Enterprise** image, vous pouvez obtenir des machines virtuelles autonomes qui contiennent des R Server. Les images sont disponibles pour la version de Linux CentOS 7.2, version de Linux RedHat 7.2 et Ubuntu version 16.04.

Pour plus d’informations, consultez [Machine Learning Server dans le Cloud](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

 > [!NOTE]
 > Ce type de nouvelle machine virtuelle remplace **RRE pour Windows Virtual Machine**, précédemment disponible dans la Place de marché Azure.

### <a name="sql-server-virtual-machines"></a>Machines virtuelles SQL Server

Il existe deux options pour l’utilisation de SQL Server d’apprentissage dans Azure :

+ Obtenir des images de machine virtuelle qui inclut SQL Server R Services préinstallé.
+ Créer une machine virtuelle Azure et installer SQL Server Édition Enterprise ou Developer à l’aide de votre propre clé de licence. 
  
    Ensuite, exécutez le programme d’installation à nouveau pour ajouter et activer le service machine learning, comme décrit ici : [l’installation de SQL Server R Services sur une machine virtuelle Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).
+ Créer une base de données SQL Azure à l’aide d’un niveau de service qui peut prendre en charge d’apprentissage et utiliser la nouvelle fonctionnalité de R Services actuellement en version préliminaire. Pour plus d’informations, consultez [base de données SQL Azure](../r/using-r-in-azure-sql-database.md).

> [!NOTE]
> Actuellement, SQL Server Machine Learning Services n'est pas pris en charge sur les ordinateurs virtuels Linux pour SQL Server 2017. Toutefois, vous pouvez effectuer sur un modèle formé à l’aide de la fonction de prédiction de T-SQL de calcul de score. Pour plus d’informations, consultez [score natif dans SQl Server](../sql-native-scoring.md). 

### <a name="virtual-machines-for-deep-learning"></a>Machines virtuelles pour en savoir plus approfondie 

Auparavant, fournis par Microsoft le Kit de formation approfondie pour les données scientifiques Machine virtuelle, qui vous pouvez ajouter à un données Science ordinateur virtuel existant. Ce kit est désormais remplacé par l’ordinateur virtuel de formation approfondie, qui contient des outils d’apprentissage approfondie populaires :

+ Éditions de GPU de formation approfondie infrastructures telles que Microsoft cognitifs Toolkit, TensorFlow, Keras et Caffe
+ Pilotes GPU intégrés
+ Un ensemble d’outils d’image et de traitement de texte
+ Outils de développement entreprise telles que Microsoft R Server Developer Edition, Anaconda, Python, blocs-notes Notebook pour Python et R
+ Outils de développement pour Python, R, SQL Server et bien plus encore
+ Exemples de bout en bout pour l’image et la présentation du texte

La machine virtuelle de profondeur apprentissage est disponible sur le 2016 de Windows ou sur les plateformes Ubuntu Linux. Pour plus d’informations, consultez [infrastructures Learning approfondie et AI](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-deep-learning-ai-frameworks).

> [!IMPORTANT]
> 
> Le déploiement de cet ordinateur virtuel requiert les images de machine virtuelle Azure GPU NC-série, qui sont disponibles dans les régions Azure limitées. Pour plus d’informations sur la disponibilité, consultez [produits disponibles par région](https://azure.microsoft.com/en-us/regions/services/). Lorsque vous configurez l’ordinateur virtuel, veillez à utiliser **HDD** en tant que le type de disque, pas **SSD**.

## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

Cette section contient des questions courantes sur les ordinateurs virtuels à partir de Microsoft d’apprentissage.

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>Puis-je installer une machine virtuelle avec SQL Server 2017 ?

Une machine virtuelle Windows pour SQL Server 2017 Enterprise Edition qui inclut des Services de Machine Learning sera bientôt disponible. Recherchez les annonces sur ces sites de blogs :

+ [Cortana Intelligence et d’apprentissage](https://blogs.technet.microsoft.com/machinelearning/)
+ [Insider de plateforme de données](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Comment accéder aux données dans un compte de stockage Azure ?

Lorsque vous avez besoin d’utiliser des données à partir de votre compte de stockage Azure, plusieurs options s’offrent à vous pour l’accès aux données ou leur déplacement :

+ Copier les données à partir de votre compte de stockage dans le système de fichiers local à l’aide d’un utilitaire, comme [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Ajoutez les fichiers vers un partage de fichiers sur votre compte de stockage, puis montez le partage de fichiers comme un lecteur réseau sur votre machine virtuelle.  Pour plus d’informations, consultez [Montage de fichiers Azure](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Comment utiliser des données à partir du stockage ADLS (Azure Data Lake Storage) ?

Vous pouvez lire des données à partir du stockage ADLS à l’aide de RevoScaleR, si vous référencez le compte de stockage la même façon que vous le feriez pour un HDFS système de fichiers, à l’aide de webHDFS.  Pour plus d’informations, consultez l’article : [à l’aide de R pour effectuer des opérations de système de fichiers sur Azure Data Lake Store](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).



