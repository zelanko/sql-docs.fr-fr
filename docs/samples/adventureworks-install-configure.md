---
title: Installer et configurer la base de données de l’échantillon d’AdventureWorks
description: Suivez ces instructions pour télécharger et installer des bases de données d’échantillons d’AdventureWorks avec SQL Server Management Studio ou dans la base de données SqL Azure.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 7fa3d199450750a444f2b67ae3e4583549d449b9
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484568"
---
# <a name="adventureworks-installation-and-configuration"></a>Installation et configuration AdventureWorks
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

AdventureWorks télécharge des liens et des instructions d’installation. 

## <a name="prerequisites"></a>Prérequis

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) ou [Azure SQL Database](https://azure.microsoft.com/services/sql-database/). Pour la version complète de l’échantillon, utilisez SQL Server Evaluation/Developer/Enterprise Edition.
- [STUDIO de gestion des serveurs SQL](../ssms/download-sql-server-management-studio-ssms.md). Pour les meilleurs résultats, utilisez la version de juin 2016 ou plus tard.
 
## <a name="oltp-downloads"></a>Téléchargements OLTP

Des liens directs vers les versions OLTP d’AdventureWorks peuvent être trouvés ci-dessous :

- [AdventureWorks2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Téléchargements Data Warehouse

Des liens directs vers les versions Data Warehouse d’AdventureWorks peuvent être trouvés ci-dessous :

- [AdventureWorksDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2.bak](https://github.com/microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-dw.bak)

## <a name="creation-scripts"></a>Scénarios de création
Les scripts ci-dessous peuvent être utilisés pour créer l’ensemble de la base de données AdventureWorks, quelle que soit la version. 

- [AdventureWorks OLTP Scripts Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [AdventureWorks DW Scripts Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="github-links"></a>Liens GitHub

- [Tous les fichiers AdventureWorks pour SQL 2014 - 2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Tous les fichiers AdventureWorks pour SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Tous les fichiers AdventureWorks pour SQL 2008 et 2008R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="install-to-sql-server"></a>Installer sur SQL Server

### <a name="restore-backup"></a>Restaurer la sauvegarde
Suivez les étapes ci-dessous pour restaurer une sauvegarde de votre base de données à l’aide de SQL Server Management Studio. 

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance sqL Server cible.
2. Cliquez à droite sur le nœud **databases** et sélectionnez **Restore Database**.
3. Sélectionnez **l’appareil** et cliquez sur les ellipses (**...**)
4. Dans le dialogue **Sélectionnez les périphériques de sauvegarde**, cliquez sur **Ajouter,** naviguer vers la sauvegarde de base de données dans le système de fichiers du serveur, et sélectionnez la sauvegarde. Cliquez sur **OK**.
5. Si nécessaire, modifiez l’emplacement cible des données et des fichiers journaux, dans la vitre **des fichiers.** Notez qu’il est préférable de placer des données et des fichiers de journal sur différents lecteurs.
6. Cliquez sur **OK**. Cela permettra d’initier la restauration de la base de données. Une fois qu’elle sera terminée, vous aurez installé la base de données AdventureWorks sur votre instance SQL Server.

Pour plus d’informations sur la restauration d’une base de données SQL Server, voir [Restaurer une sauvegarde de base de données à l’aide de SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Joindre un fichier de données
Suivez les étapes ci-dessous pour joindre le fichier de données de votre base de données à l’aide de SQL Server Management Studio.

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance sqL Server cible.
2. Cliquez à droite sur le nœud **databases,** et **sélectionnez Attach**.
3. Sélectionnez **Ajouter** et naviguer vers le . Fichier MDF que vous souhaitez joindre. 
1. Sélectionnez le fichier et cliquez sur **OK**. 
    1. La base de données que vous avez sélectionnée doit être affichée dans la fenêtre inférieure. Si le fichier est répertorié comme "non trouvé", sélectionnez les ellipses (**...**) à côté du nom du fichier et mettre à jour le chemin vers le chemin correct. 
    1. Si vous n’avez que le fichier de données (.mdf), et non le fichier journal (.ldf), puis mettre en évidence le .ldf dans la fenêtre inférieure et sélectionnez **Supprimer**. Cela créera un nouveau fichier journal. 
1. Sélectionnez **OK** pour joindre le fichier. Une fois le fichier joint, vous aurez installé la base de données AdventureWorks sur votre instance SQL Server.  

Pour plus d’informations sur la fixation des fichiers de base de données, voir [Joindre une base de données](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Installer à Azure SQL Database


Si vous n’avez pas encore de serveur SQL à Azure, naviguez vers le [portail Azure](https://portal.azure.com/) et créez une nouvelle base de données SQL. Dans le processus de création d’une base de données, vous allez créer un serveur. Prenez note du serveur. Voir [ce tutoriel](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) pour créer une base de données en quelques minutes.

1. Connectez-vous à votre portail Azure.
1. Sélectionnez **Créez une ressource** en haut à gauche de la vitre de navigation. 
1. Sélectionnez **Bases de données**, puis **Base de données SQL**. 
1. Entrez les informations demandées.
1. Dans le domaine **Select Source,** sélectionnez **Sample (AdventureWorksLT)** pour restaurer une sauvegarde de la dernière sauvegarde AdventureWorksLT.
1. Sélectionnez **Créer** pour créer votre nouvelle base de données SQL, qui est la copie restaurée de la base de données AdventureWorksLT. 


## <a name="see-also"></a>Voir aussi
[Tutoriels pour SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[Tutorials pour le moteur de base de données SQL Server](../relational-databases/database-engine-tutorials.md)
