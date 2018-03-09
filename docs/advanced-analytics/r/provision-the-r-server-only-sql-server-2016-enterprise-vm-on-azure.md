---
title: "Configurer un ordinateur virtuel pour l’apprentissage sur Azure | Documents Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 62e1c347a3c5ee110e6865cd8c13ade76ba62b80
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Configurer un ordinateur virtuel pour l’apprentissage sur Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Machines virtuelles sur Azure sont une option pratique pour la configuration rapidement d’un environnement de serveur complet pour les solutions d’apprentissage.

Cet article répertorie les images de machine virtuelle contenant SQL Server avec l’apprentissage automatique, ainsi que certains ordinateurs virtuels liés.

Cet article fournit également des réponses aux questions courantes sur la modification ou la mise à niveau une instance existante de SQL Server dans une machine virtuelle.

+ [Liste d’ordinateurs virtuels en cours](#bkmk_list)

## <a name="provision-a-virtual-machine-with-sql-server-and-machine-learning"></a>Configurer une machine virtuelle avec SQL Server et d’apprentissage

Si vous ne connaissez pas à l’aide de machines virtuelles Azure, nous recommandons que vous consultez les articles suivants pour plus d’informations sur l’utilisation du portail et de configurer une machine virtuelle.

+ [Prise en main des machines virtuelles](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Mise en route avec les Machines virtuelles Windows](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

Veillez à utiliser la nouvelle version du portail Azure ou Azure Marketplace. Certaines images ne sont pas disponibles lorsque vous parcourez la galerie Azure sur le portail classique.

**Créer la machine virtuelle**

1. Ouvrez le portail Azure : [portal.azure.com](https:portal.azure.com).

2. Cliquez sur **virtuels**, ou cliquez sur **nouveau**.

3. Cliquez sur **Ajouter**.

4. Dans la zone de recherche en haut de la page, tapez « Serveur d’apprentissage Machine » ou « SQL Server » pour afficher une liste d’ordinateurs virtuels associés.

5. Passez en revue la configuration requise, puis cliquez sur **Create** prise en main.

6. Une fois l’ordinateur virtuel a été créé et est en cours d’exécution, cliquez sur le **Connect** bouton pour ouvrir une connexion et de se connecter au nouvel ordinateur.

5. Une fois que vous vous connectez, vous pouvez installer des packages R ou Python supplémentaires ou configurer votre outil de développement par défaut.

### <a name="connect-to-the-virtual-machine"></a>Se connecter à la machine virtuelle

La manière de qu'un client se connecte à SQL Server s’exécutant sur un ordinateur virtuel diffère selon l’emplacement du client et la configuration du réseau.

Pour plus d’informations, consultez [se connecter à un ordinateur virtuel de SQL Server sur Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-connect).

## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

Cette section contient des questions courantes sur les ordinateurs virtuels à partir de Microsoft d’apprentissage.

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>Puis-je installer une machine virtuelle avec SQL Server 2017 ?

Une machine virtuelle Windows pour SQL Server 2017 Enterprise Edition qui inclut des Services de Machine Learning est disponible à partir de novembre 2017. 

Pour les annonces sur les nouveaux ordinateurs virtuels de science des données, regardez ces sites de blog :

+ [Cortana Intelligence et l’apprentissage](https://blogs.technet.microsoft.com/machinelearning/)
+ [Insider de plateforme de données](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="adding-sql-server-to-an-existing-virtual-machine"></a>Ajout de SQL Server à un ordinateur virtuel existant

Outre la création d’un ordinateur virtuel à l’aide une image qui inclut déjà SQL Server d’apprentissage automatique, vous pouvez installer SQL Server sur un ordinateur virtuel existant et activer les fonctionnalités d’apprentissage automatique. Nous vous recommandons l’édition Enterprise ou Developer, afin d’éviter les contraintes de ressources. L’installation requiert également que vous utilisez votre propre clé de licence.

Lorsque vous exécutez le programme d’installation, veillez à sélectionner les fonctionnalités et au moins une langue (R ou Python) d’apprentissage automatique. Quelques étapes supplémentaires sont nécessaires pour activer les services d’apprentissage machine pour communiquer avec SQL Server et pour activer la mise en réseau sur l’ordinateur virtuel.

Pour plus d’informations, consultez [l’installation de SQL Server R Services sur une machine virtuelle Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

### <a name="using-machine-learning-in-azure-sql-database"></a>À l’aide d’apprentissage dans la base de données SQL Azure

Actuellement, la version préliminaire de la prise en charge de R dans SQL Azure est interrompue en cours de développement. Pour plus d’informations, consultez [base de données SQL Azure](../r/using-r-in-azure-sql-database.md).

### <a name="can-i-upgrade-the-sql-server-version-on-a-virtual-machine"></a>Puis-je mettre à niveau la version de SQL Server sur un ordinateur virtuel ?

Bien que les images de SQL Server 2016 prend en charge R, si vous souhaitez utiliser Python, vous pouvez mettre à niveau vers SQL Server 2017, laquelle met également à niveau des autres composants d’apprentissage.

Pour mettre à jour la version de SQL Server qui est installée, ouvrez le centre d’Installation SQL Server sur l’ordinateur virtuel, puis sélectionnez le **mise à niveau** option. En fonction de laquelle vous avez créé, une licence peut être nécessaire.

Pour plus d’informations, consultez [mise à niveau de SQL Server à l’aide de l’Assistant installation](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup).

### <a name="can-i-upgrade-just-the-machine-learning-components"></a>Puis-je mettre à niveau uniquement les composants d’apprentissage automatique ?

Lorsque des mises à niveau sont publiés pour RevoScaleR, MicrosoftML ou revoscalepy, vous pouvez mettre à niveau les composants utilisés par SQL Server, à l’aide d’un processus appelé d’apprentissage automatique _liaison_. Cela ne modifie pas votre version de SQL Server, mais il ne modifie pas la stratégie de prise en charge pour l’instance.

Pour plus d’informations, consultez [SqlBindR utilisé pour mettre à niveau les composants de la machine learning sur SQL Server](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Comment accéder aux données dans un compte de stockage Azure ?

Lorsque vous avez besoin d’utiliser des données à partir de votre compte de stockage Azure, plusieurs options s’offrent à vous pour l’accès aux données ou leur déplacement :

+ Copier les données à partir de votre compte de stockage dans le système de fichiers local à l’aide d’un utilitaire, comme [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Ajoutez les fichiers vers un partage de fichiers sur votre compte de stockage, puis montez le partage de fichiers comme un lecteur réseau sur votre machine virtuelle. Pour plus d’informations, consultez [Montage de fichiers Azure](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Comment utiliser des données à partir du stockage ADLS (Azure Data Lake Storage) ?

Vous pouvez lire des données à partir du stockage ADLS à l’aide de RevoScaleR, à l’aide de webHDFS pour référencer le système de fichiers de la même façon que vous le feriez pour un HDFS de compte de stockage. Pour plus d’informations, consultez l’article : [à l’aide de R pour effectuer des opérations de système de fichiers sur Azure Data Lake Store](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).

### <a name="i-cant-find-the-rre-virtual-machine"></a>Impossible de trouver l’ordinateur virtuel RRE

La « RRE pour Machine virtuelle Windows », qui était précédemment disponible dans Azure Marketplace a été remplacé par l’image « Machine Learning pour Windows Server ».

Images de machine Learning serveur sont également disponibles pour Linux CentOS version 7.2, version de Linux RedHat 7.2 et Ubuntu version 16.04.

Pour plus d’informations, consultez [Machine Learning Server dans le Cloud](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

### <a name="configuring-machine-learning-server-or-r-server-to-support-web-services"></a>Configuration de Machine Learning Server ou R Server pour prendre en charge des services web

Si vous utilisez un ordinateur virtuel qui inclut le serveur de Machine Learning, une configuration supplémentaire peut être nécessaire pour déployer le service web, l’exécution à distance, ou pour utiliser la machine virtuelle comme un serveur de déploiement de votre organisation.

Pour obtenir des instructions, consultez [configuration du serveur de Machine Learning pour opérationnaliser analytique](https://docs.microsoft.com/machine-learning-server/operationalize/configure-machine-learning-server-one-box).

Une configuration supplémentaire n’est pas nécessaire si vous souhaitez simplement utiliser les packages tels que RevoScaleR ou MicrosoftML.

## <a name="bkmk_list"></a>Liste des machines virtuelles

Actuellement, les ordinateurs virtuels suivants sont disponibles pour l’apprentissage avec SQL Server :

|Nom| Commentaires|
|----|----|----|
| **SQL Server 2016**| ***  |
|SQL Server 2016 SP1 Enterprise sur Windows|R Services d’analytique avancée intégrées.|
|BYOL SQL Server 2016 SP1 Enterprise sur Windows Server |R Services d’analytique avancée intégrées. |
|Licence gratuite : Développeur SQL Server 2016 SP1 sur Windows Server 2016 |R Services d’analytique avancée intégrées. |
| Machine virtuelle de science des données - Windows 2012|Contient les outils courants pour la science des données, y compris Microsoft R Server Developer Edition, SQL Server 2016 Developer edition, la distribution de Python de Anaconda, édition développeur de Julia Pro et Notebook blocs-notes pour R.| 
| Machine virtuelle de science des données - 2016 de Windows|Inclut SQL Server 2016 Developer Edition, avec prise en charge pour l’analytique de R dans base de données.|
|**SQL Server 2017**| ***   |
|SQL Server 2017 Enterprise Windows Server 2016| Machine Learning Services avec prise en charge de langage Python et R.|
|BYOL SQL Server 2017 Enterprise Windows Server 2016|Machine Learning Services avec prise en charge de langage Python et R.|
| Licence de serveur SQL libre : Développeur SQL Server 2017 sur Windows Server|Machine Learning Services avec prise en charge de langage Python et R.|
| **Autres**| *** |
| Serveur uniquement SQL Server 2017 Enterprise d’apprentissage|Similaire à l’image de SQL Server 2016 Enterprise, mais contient la version autonome du serveur de Machine Learning de cœur ScaleR et des fonctionnalités à l’Opérationnalisation optimisé pour Windows, les environnements.|
| Serveur d’apprentissage pour Windows|Contient la version autonome de Machine Learning Server, avec les fonctionnalités à l’Opérationnalisation optimisées pour les environnements Windows.|
|Machine virtuelle de science des données |Les éditions de Linux incluent R Server. Les ordinateurs virtuels Linux qui incluent SQL Server 2017 ne peut pas exécuter le code R ou Python dans SQL Server. Toutefois, vous pouvez effectuer sur un modèle formé à l’aide de la fonction de prédiction de T-SQL de calcul de score. Pour plus d’informations, consultez [score natif dans SQl Server](../sql-native-scoring.md).|
