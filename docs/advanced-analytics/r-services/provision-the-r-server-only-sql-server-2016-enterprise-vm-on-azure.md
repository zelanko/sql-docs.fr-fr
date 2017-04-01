---
title: "Approvisionner la machine virtuelle R Server (Only) SQL Server 2016 Enterprise sur Azure | Microsoft Docs"
ms.custom: ""
ms.date: "12/22/2016"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 5
---
# Approvisionner la machine virtuelle R Server (Only) SQL Server 2016 Enterprise sur Azure

La machine virtuelle R Server (Only) SQL Server 2016 Enterprise sur Azure est une nouvelle option assurant la configuration rapide et simple d’un environnement de serveur pour prendre en charge les solutions R. Cette machine virtuelle Azure a été préconfigurée avec Microsoft R Server (Standalone). 

Cette nouvelle machine virtuelle remplace RRE pour Windows Virtual Machine, précédemment disponible dans la Place de marché Azure. 

Cette machine virtuelle inclut également DeployR Enterprise, pour le déploiement de l’analytique R à l’intérieur d’applications et des systèmes principaux. Pour plus d’informations, consultez [À propos de Deploy R](https://msdn.microsoft.com/microsoft-r/deployr-about).


## Approvisionner la machine virtuelle R Server

Si vous n’êtes pas familiarisé avec l’utilisation des machines virtuelles Azure, nous vous recommandons de consulter cet article pour plus d’informations sur l’utilisation du portail et la configurer d’une machine virtuelle.
[Prise en main des machines virtuelles](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)

Pour créer la machine virtuelle R Server à partir de la Place de marché Microsoft Azure 
1. Cliquez sur **Machines virtuelles** et, dans la zone de recherche, tapez *R Server*.
2. Sélectionnez **R Server Only SQL Server 2016 Enterprise**
3. Continuez à approvisionner la machine virtuelle, comme décrit dans l’article à l’adresse [https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/) 
7. Une fois que la machine virtuelle a été créée et est en cours d’exécution, cliquez sur le bouton **Connecter** pour ouvrir une connexion et accéder à la nouvelle machine.
8. Lorsque vous vous connectez, **Server Manager** est ouvert par défaut, mais aucune configuration de serveur supplémentaire n’est requise. Fermez **Server Manager** pour accéder au bureau, et poursuivez avec les étapes suivantes :
    + Installation d’outils R supplémentaires ou d’outils de développement
    + Configuration de DeployR  

Pour localiser la machine virtuelle R Server dans le Portail Azure Classic
1. Cliquez sur **Machines virtuelles**, puis cliquez sur **NOUVEAU**.
2. Dans le volet **Nouveau**, les options **Calcul** et **Machine virtuelle** doivent déjà être sélectionnées. 
3. Cliquez sur **Depuis la galerie** pour localiser l’image de la machine virtuelle. Vous pouvez taper *R Server* dans la zone de recherche ou cliquer sur **Microsoft**. Ensuite, faites défiler vers le bas jusqu’à atteindre **R Server Only SQL Server 2016 Enterprise**.


## Installer les outils R
Par défaut, Microsoft R Server inclut tous les outils R installés avec une installation basique de R, notamment RTerm et RGui. Un raccourci vers RGui a été ajouté sur le bureau, si vous souhaitez prendre en main R immédiatement.

Toutefois, vous souhaiterez peut-être installer les outils R supplémentaires, notamment RStudio, les outils R pour Visual Studio ou Microsoft R Client. Consultez les liens suivants pour les emplacements et instructions de téléchargement :
+ [Outils R pour Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio pour Windows](https://www.rstudio.com/products/rstudio/download/)

Une fois que vous avez installé ces outils, veillez à orienter vos outils vers les bibliothèques R Server.

## Utilisation de DeployR sur la machine virtuelle

Quelques étapes supplémentaires sont requises pour utiliser l’instance de DeployR qui est installée sur cette machine virtuelle. 

Pour configurer l’instance de DeployR :

1. Sur la machine virtuelle, ouvrez **l’utilitaire d’administration de DeployR**.
2. Définissez le mot de passe d’administration de DeployR comme indiqué dans la rubrique [Étapes consécutives à l’installation](https://msdn.microsoft.com/microsoft-r/deployr-install-on-windows)
3. Définissez le contexte web DeployR. Pour plus d’informations, consultez [Installation de l’administration de DeployR dans le Cloud](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud) 
4. Ouvrez les ports appropriés sur la machine virtuelle comme indiqué dans la rubrique [Configuration des points de terminaison Azure](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#configuring-azure-endpoints) 
4. Mettez à jour le pare-feu Windows comme indiqué dans la rubrique [Mise à jour du pare-feu](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#updating-the-firewall) 

## Accès aux données dans un compte de stockage Azure 

Lorsque vous avez besoin d’utiliser des données à partir de votre compte de stockage Azure, plusieurs options s’offrent à vous pour l’accès aux données ou leur déplacement :


+ Copier les données à partir de votre compte de stockage dans le système de fichiers local à l’aide d’un utilitaire, comme [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Ajoutez les fichiers vers un partage de fichiers sur votre compte de stockage, puis montez le partage de fichiers comme un lecteur réseau sur votre machine virtuelle.  Pour plus d’informations, consultez [Montage de fichiers Azure](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/). 

## Utilisation des données dans un compte de stockage Azure Data Lake Storage (ADLS)

Vous pouvez lire des données à partir du stockage ADLS à l’aide de ScaleR, si vous référencez le compte de stockage de la même manière que vous le feriez pour un système de fichiers HDFS, à l’aide de webHDFS.  Pour plus d’informations, consultez ce [guide d’installation](http://go.microsoft.com/fwlink/?LinkId=723452).

## Ressources

Vous trouverez de la documentation supplémentaire sur Microsoft R dans la bibliothèque MSDN : [R Server et Scale R](https://msdn.microsoft.com/microsoft-r)  


Consultez ces ressources supplémentaires pour en savoir plus sur R en général : 
+ [DataCamp](http://www.datacamp.com) Fournit une présentation et une formation intermédiaire gratuite dans R, ainsi qu’une formation sur l’utilisation du Big Data à l’aide de Revolution R.
+ [Stack Overflow](http://www.stackoverflow.com) Bonne ressource pour la programmation de R et les questions relatives aux outils ML. 
+ [Cross Validated](https://stats.stackexchange.com/) Site pour les questions concernant les problèmes statistiques en Machine Learning.
+ [Archives de liste de distribution d’aide sur R](https://www.r-project.org/mail.html) Bonne ressource pour les informations historiques. 
+ [Site web MRAN](https://mran.microsoft.com/documents/getting-started/) Nombreuses autres ressources R.  

## Voir aussi
[SQL Server R Services](https://msdn.microsoft.com/library/mt604845.aspx)
