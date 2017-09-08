---
title: Approvisionner la machine virtuelle R Server (Only) SQL Server 2016 Enterprise sur Azure
ms.custom: 
ms.date: 06/05/2017
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3bfca0753984f09220d8ca4e4f6933c949daf2b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="advanced-analytics-virtual-machines-on-azure"></a>Machines virtuelles d’Analytique avancée sur Azure

Machines virtuelles sur Azure sont une option pratique pour la configuration rapidement d’un environnement de serveur complet pour les solutions d’apprentissage. Cette rubrique répertorie certaines images de machine virtuelle contenant R Server, SQL Server avec l’apprentissage ou autres outils de science des données à partir de Microsoft.

> [!TIP]
> Nous vous recommandons d’utiliser la nouvelle version du portail Azure et Azure Marketplace. Certaines images ne sont pas disponibles lorsque vous parcourez la galerie Azure sur le portail classique.

Azure Marketplace contient plusieurs ordinateurs virtuels qui prennent en charge la science des données. Cette liste n’est pas destinée à être complète, mais uniquement de fournir les noms des images qui incluent l’apprentissage des services, pour faciliter la découverte de l’ordinateur Microsoft R Server ou SQL Server.

## <a name="how-to-provision-a-vm"></a>Comment configurer une machine virtuelle

Si vous ne connaissez pas à l’aide de machines virtuelles Azure, nous recommandons que vous consultez les articles suivants pour plus d’informations sur l’utilisation du portail et de configurer une machine virtuelle.

+ [Prise en main des machines virtuelles](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Prise en main des Machines virtuelles Windows](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/)

### <a name="find-an-image"></a>Rechercher une image

1. Dans le tableau de bord Azure, cliquez sur **Marketplace**.

    - Cliquez sur **Intelligence et analytique** ou **bases de données**, puis tapez « R » dans le **filtre** contrôle pour afficher une liste d’ordinateurs virtuels R Server.
    - Autres possible des chaînes pour le **filtre** contrôle sont *science des données* et *apprentissage*
    - Utilisez le caractère générique % dans la recherche pour rechercher les noms de machine virtuelle qui contiennent une chaîne cible, tels que *R* ou *Julia*.

2. Pour obtenir les R Server pour Windows, sélectionnez **R Server uniquement SQL Server 2016 Enterprise**.
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) est concédé sous licence comme une fonctionnalité de SQL Server Enterprise Edition, mais la version 9.1. est installé comme serveur autonome et traité sous la stratégie de prise en charge du cycle de vie moderne.

3. Une fois que la machine virtuelle a été créée et est en cours d’exécution, cliquez sur le bouton **Connecter** pour ouvrir une connexion et accéder à la nouvelle machine.

4. Une fois que vous vous connectez, vous devrez peut-être installer les outils R supplémentaires ou des outils de développement.

### <a name="install-additional-r-tools"></a>Installer les outils R supplémentaires

Par défaut, Microsoft R Server inclut tous les outils R installés avec une installation basique de R, notamment RTerm et RGui. Un raccourci vers RGui a été ajouté sur le bureau, si vous souhaitez prendre en main R immédiatement.

Toutefois, vous avez tout intérêt à installer les outils R supplémentaires, tels que RStudio, les outils R pour Visual Studio (RTV) ou Microsoft R Client. Consultez les liens suivants pour les emplacements et instructions de téléchargement :
+ [Outils R pour Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio pour Windows](https://www.rstudio.com/products/rstudio/download/)

Une fois l’installation terminée, veillez à changer l’emplacement du runtime R par défaut pour que tous les outils de développement R utilisent les bibliothèques Microsoft R Server.

### <a name="configure-server-for-web-services"></a>Configurer le serveur pour les services web

Si la machine virtuelle inclut R Server, une configuration supplémentaire est nécessaire pour utiliser le déploiement de service web ou l’exécution à distance, ou pour utiliser R Server comme serveur de déploiement dans votre organisation. Pour obtenir des instructions, consultez [Configure R Server for Operationalization](https://msdn.microsoft.com/microsoft-r/operationalize/configuration-initial) (Configurer R Server pour le rendre opérationnel).

> [!NOTE]
> Une configuration supplémentaire n’est pas nécessaire si vous souhaitez simplement utiliser les packages tels que RevoScaleR ou MicrosoftML.

## <a name="r-server-images"></a>Images de serveur R

### <a name="microsoft-data-science-virtual-machine"></a>Machine virtuelle pour la science des données Microsoft

Est configurée avec Microsoft R Server, ainsi que Python (distribution Anaconda), un serveur jupyter Notebook, Visual Studio Community Edition, Power BI Desktop, le Kit de développement logiciel Azure et SQL Server Express edition.

La version de Windows s’exécute sur Windows Server 2012 et contient de nombreux outils spéciaux pour la modélisation et analytique, y compris CNTK et mxnet, les packages R populaires tels que xgboost et Vowpal Wabbit.

### <a name="linux-data-science-virtual-machine"></a>Machine virtuelle de science des données Linux

Contient également des outils courants pour les activités développement et de la science des données, y compris les ordinateurs portables Microsoft R Open, Microsoft R Server Developer Edition, Anaconda Python et Notebook pour Python, R et Julia.

Cette image de machine virtuelle a été récemment mis à jour pour inclure JupyterHub, logiciel open source qui permet l’utilisation par plusieurs utilisateurs, via différentes méthodes d’authentification, notamment l’authentification de compte locale du système d’exploitation et l’authentification de compte Github. JupyterHub est une option particulièrement utile si vous voulez exécuter une classe de formation et que tous les étudiants pour partager le même serveur, mais utilisez des blocs-notes et des répertoires.

Les images sont fournis pour Ubuntu, Centos et Centos CSP.

### <a name="r-server-only-sql-server-2016-enterprise"></a>R Server uniquement SQL Server 2016 Enterprise

Cette machine virtuelle inclut un programme d’installation autonome pour [R Server 9.1.](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) qui prend en charge le nouveau modèle de licence du cycle de vie logiciel moderne.

 R Server est également disponible dans les images pour Linux CentOS version 7.2, version de Linux RedHat 7.2 et Ubuntu version 16.04.

 > [!NOTE]
 > Ce type de nouvelle machine virtuelle remplace **RRE pour Windows Virtual Machine**, précédemment disponible dans la Place de marché Azure.

## <a name="sql-server-images"></a>Images de SQL Server

Pour utiliser R Services (de-de base de données) ou Machine Learning Services, vous devez installer un des ordinateurs SQL Server Enterprise ou Developer edition virtuels et ajouter le service machine learning, comme décrit ici : [l’installation de SQL Server R Services sur une Machine virtuelle de Azure](../../advanced-analytics/r-services/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

> [!NOTE]
> Actuellement, les services de machine learning ne sont pas pris en charge sur les ordinateurs virtuels Linux pour SQL Server 2017, ou dans la base de données SQL Azure. Vous devez utiliser SQL Server 2016 SP1 ou SQL Server 2017 pour Windows.

La Machine virtuelle de science des données inclut également SQL Server 2016 avec la fonctionnalité des services R déjà activée.


## <a name="other-vms"></a>Autres machines virtuelles

### <a name="deep-learning-toolkit-for-the-data-science-virtual-machine"></a>Kit de formation pour la Machine virtuelle de science des données de profondeur

Cet ordinateur virtuel contient le même ordinateur que celui disponible sur l’ordinateur virtuel de science des données, des outils d’apprentissage, mais avec des versions GPU de mxnet, CNTK, TensorFlow et Keras. Cette image peut être utilisée uniquement sur les instances de la série de GPU N Azure. 

Le Kit de formation approfondie fournit également un jeu d’exemples approfondie des solutions qui utilisent le GPU, y compris la reconnaissance d’image sur la base de données CIFAR-10 et un exemple de reconnaissance de caractères sur la base de données MNIST d’apprentissage. Les instances GPU sont actuellement disponibles en Amérique du Sud, est des États-Unis, Europe de l’ouest et Asie du Sud-est.

> [!IMPORTANT]
> Les instances GPU sont actuellement disponibles uniquement dans le Centre-Sud des États-Unis.


## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>Puis-je installer une machine virtuelle avec SQL Server 2017 ?

Les images sont disponibles qui contiennent SQL Server 2017 CTP 2.0 pour les environnements Linux, mais ces environnements ne prennent actuellement pas en charge les Services de Machine Learning. 

Une machine virtuelle Windows pour SQL Server 2017 Enterprise Edition qui inclut des Services de Machine Learning seront plus disponible après la publication. 

En guise d’alternative, vous pouvez utiliser l’image de SQL Server 2016 et mettre à niveau votre instance de R, comme décrit ici : [mettre à niveau une Instance à l’aide de SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). 

Ou bien, créez une machine virtuelle et télécharger la version préliminaire CTP 2.0 [SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-2017).

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Comment accéder aux données dans un compte de stockage Azure ?

Lorsque vous avez besoin d’utiliser des données à partir de votre compte de stockage Azure, plusieurs options s’offrent à vous pour l’accès aux données ou leur déplacement :

+ Copier les données à partir de votre compte de stockage dans le système de fichiers local à l’aide d’un utilitaire, comme [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Ajoutez les fichiers vers un partage de fichiers sur votre compte de stockage, puis montez le partage de fichiers comme un lecteur réseau sur votre machine virtuelle.  Pour plus d’informations, consultez [Montage de fichiers Azure](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Comment utiliser des données à partir du stockage ADLS (Azure Data Lake Storage) ?

Vous pouvez lire des données à partir du stockage ADLS à l’aide de RevoScaleR, si vous référencez le compte de stockage la même façon que vous le feriez pour un HDFS système de fichiers, à l’aide de webHDFS.  Pour plus d’informations, consultez l’article : [à l’aide de R pour effectuer des opérations de système de fichiers sur Azure Data Lake Store](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).

## <a name="see-also"></a>Voir aussi

[SQL Server R Services](https://msdn.microsoft.com/library/mt604845.aspx)


