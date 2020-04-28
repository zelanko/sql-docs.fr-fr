---
title: Installer et configurer l’exemple de base de données AdventureWorks
description: Suivez ces instructions pour télécharger et installer des exemples de bases de données AdventureWorks avec SQL Server Management Studio ou dans Azure SQL Database.
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81484568"
---
# <a name="adventureworks-installation-and-configuration"></a>Installation et configuration d’AdventureWorks
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Liens de téléchargement AdventureWorks et instructions d’installation. 

## <a name="prerequisites"></a>Prérequis

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) ou [Azure SQL Database](https://azure.microsoft.com/services/sql-database/). Pour obtenir la version complète de l’exemple, utilisez l’édition Évaluation SQL Server/Developer/Enterprise.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Pour obtenir les meilleurs résultats, utilisez la version du 2016 juin ou une version ultérieure.
 
## <a name="oltp-downloads"></a>Téléchargements OLTP

Vous trouverez ci-dessous des liens directs vers les versions OLTP d’AdventureWorks :

- [AdventureWorks2017. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Téléchargements de Data Warehouse

Vous trouverez ci-dessous des liens directs vers les versions Data Warehouse d’AdventureWorks :

- [AdventureWorksDW2017. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2. bak](https://github.com/microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-dw.bak)

## <a name="creation-scripts"></a>Scripts de création
Les scripts ci-dessous peuvent être utilisés pour créer l’intégralité de la base de données AdventureWorks, quelle que soit la version. 

- [Zip des scripts OLTP AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [Zip des scripts AdventureWorks DW](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="github-links"></a>Liens GitHub

- [Tous les fichiers AdventureWorks pour SQL 2014-2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Tous les fichiers AdventureWorks pour SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Tous les fichiers AdventureWorks pour SQL 2008 et 2008R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="install-to-sql-server"></a>Installer sur SQL Server

### <a name="restore-backup"></a>Restaurer la sauvegarde
Suivez les étapes ci-dessous pour restaurer une sauvegarde de votre base de données à l’aide de SQL Server Management Studio. 

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance de SQL Server cible.
2. Cliquez avec le bouton droit sur le nœud **bases de données** , puis sélectionnez **restaurer la base de données**.
3. Sélectionnez l' **appareil** et cliquez sur les points de suspension (**...**)
4. Dans la boîte de dialogue **Sélectionner les unités de sauvegarde**, cliquez sur **Ajouter**, accédez à la sauvegarde de la base de données dans le système de fichiers du serveur, puis sélectionnez la sauvegarde. Cliquez sur **OK**.
5. Si nécessaire, modifiez l’emplacement cible pour les fichiers de données et les fichiers journaux dans le volet **fichiers** . Notez qu’il est recommandé de placer les fichiers de données et les fichiers journaux sur des lecteurs différents.
6. Cliquez sur **OK**. La restauration de la base de données est lancée. Une fois l’opération terminée, la base de données AdventureWorks est installée sur votre instance SQL Server.

Pour plus d’informations sur la restauration d’une base de données SQL Server, consultez [restaurer une sauvegarde de base de données à l’aide de SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Attacher un fichier de fichier
Suivez les étapes ci-dessous pour attacher le fichier de données de votre base de données à l’aide de SQL Server Management Studio.

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance de SQL Server cible.
2. Cliquez avec le bouton droit sur le nœud **bases de données** , puis sélectionnez **attacher**.
3. Sélectionnez **Ajouter** et accédez à. Fichier MDF que vous souhaitez attacher. 
1. Sélectionnez le fichier et cliquez sur **OK**. 
    1. La base de données que vous avez sélectionnée doit s’afficher dans la fenêtre inférieure. Si le fichier est listé comme « introuvable », sélectionnez les points de suspension (**...**) en regard du nom de fichier et mettez à jour le chemin d’accès vers le chemin d’accès correct. 
    1. Si vous ne disposez que du fichier de données (. mdf) et non du fichier journal (. ldf), mettez en surbrillance le fichier. ldf dans la fenêtre inférieure, puis sélectionnez **supprimer**. Un nouveau fichier journal est créé. 
1. Sélectionnez **OK** pour joindre le fichier. Une fois le fichier joint, la base de données AdventureWorks est installée sur votre instance SQL Server.  

Pour plus d’informations sur l’attachement de fichiers de base de données, consultez [attacher une base de données](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Installer sur Azure SQL Database


Si vous n’avez pas encore de SQL Server dans Azure, accédez au [portail Azure](https://portal.azure.com/) et créez un SQL Database. Lors du processus de création d’une base de données, vous allez créer un serveur. Notez le serveur. Consultez [ce didacticiel](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) pour créer une base de données en quelques minutes.

1. Connectez-vous à votre Portail Azure.
1. Sélectionnez **créer une ressource** dans le coin supérieur gauche du volet de navigation. 
1. Sélectionnez **Bases de données**, puis **Base de données SQL**. 
1. Entrez les informations demandées.
1. Dans le champ **Sélectionner une source** , sélectionnez **exemple (AdventureWorksLT)** pour restaurer une sauvegarde de la dernière sauvegarde AdventureWorksLT.
1. Sélectionnez **créer** pour créer votre SQL Database, qui est la copie restaurée de la base de données AdventureWorksLT. 


## <a name="see-also"></a>Voir aussi
[Didacticiels pour SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[Didacticiels pour le moteur de base de données SQL Server](../relational-databases/database-engine-tutorials.md)
