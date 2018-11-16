---
title: Installer et configurer la base de données AdventureWorks - SQL | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e7881400c3e4696426b1999229e917630cf905d0
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657509"
---
# <a name="adventureworks-installation-and-configuration"></a>Installation d’AdventureWorks et la configuration
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

AdventureWorks télécharger des liens et des instructions d’installation. 

## <a name="prerequisites"></a>Prérequis

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) ou [base de données SQL Azure](https://azure.microsoft.com/services/sql-database/). Pour obtenir la version complète de l’exemple, utilisez SQL Server Evaluation/développeur/Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Pour de meilleurs résultats, utilisez la version de juin 2016 ou version ultérieure.
 
## <a name="github-links"></a>Liens Github

- [Tous les fichiers AdventureWorks pour SQL 2014-2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Tous les fichiers AdventureWorks pour SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Tous les fichiers AdventureWorks pour SQL 2008 et 2008 R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="oltp-downloads"></a>Téléchargements OLTP

Vous trouverez des liens directs vers les versions OLTP d’AdventureWorks ci-dessous :

- [AdventureWorks2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Téléchargements de l’entrepôt de données

Vous trouverez des liens directs vers les versions de l’entrepôt de données d’AdventureWorks ci-dessous :

- [AdventureWorksDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008-dw.bak)

## <a name="creation-scripts"></a>Scripts de création
Les scripts ci-dessous peut être utilisé pour créer la base de données AdventureWorks entière, quelle que soit la version. 

- [Zip des Scripts OLTP d’AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [Zip des Scripts AdventureWorks DW](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="install-to-sql-server"></a>Installation de SQL Server

### <a name="restore-backup"></a>Restaurer la sauvegarde
Suivez les étapes ci-dessous pour restaurer une sauvegarde de votre base de données à l’aide de SQL Server Management Studio. 

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance de SQL Server cible.
2. Avec le bouton droit sur le **bases de données** nœud, puis sélectionnez **Restore Database**.
3. Sélectionnez **appareil** et cliquez sur le bouton de sélection (**...** )
4. Dans la boîte de dialogue **sélectionner les unités de sauvegarde**, cliquez sur **ajouter**, accédez à la sauvegarde de base de données dans le système de fichiers du serveur et sélectionnez la sauvegarde. Cliquez sur **OK**.
5. Si nécessaire, modifiez l’emplacement cible pour les données et fichiers journaux, dans le **fichiers** volet. Notez qu’il est recommandé de placer des données et fichiers journaux sur des lecteurs différents.
6. Cliquez sur **OK**. Ceci lancera la restauration de base de données. Une fois terminé, vous aurez la base de données AdventureWorks installée sur votre instance de SQL Server.

Pour plus d’informations sur la restauration d’une base de données SQL Server, consultez [restaurer une sauvegarde de base de données à l’aide de SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Attacher un fichier de données
Suivez les étapes ci-dessous pour attacher le fichier de données pour votre base de données à l’aide de SQL Server Management Studio.

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance de SQL Server cible.
2. Avec le bouton droit sur le **bases de données** nœud, puis sélectionnez **attacher**.
3. Sélectionnez **ajouter** et accédez à la. Vous souhaitez joindre un fichier MDF. 
1. Sélectionnez le fichier et cliquez sur **OK**. 
    1. La base de données que vous avez sélectionné doit être affiché dans la fenêtre inférieure. Si le fichier est répertorié comme « not found », sélectionnez les points de suspension (**...** ) en regard du nom de fichier et mise à jour le chemin d’accès pour le chemin correct. 
    1. Si vous avez uniquement le fichier de données (.mdf) et pas le fichier journal (.ldf), puis mettez en surbrillance le .ldf dans la fenêtre du bas et sélectionnez **supprimer**. Cela créera un nouveau fichier journal. 
1. Sélectionnez **OK** pour joindre le fichier. Une fois que le fichier est attaché, vous aurez la base de données AdventureWorks installée sur votre instance de SQL Server.  

Pour plus d’informations sur l’attachement de fichiers de base de données, consultez [attacher une base de données](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Installer à la base de données SQL Azure


Si vous n’avez pas encore d’un serveur SQL Server dans Azure, accédez à la [Azure portal](https://portal.azure.com/) et créer une base de données SQL. En cours de créer une base de données, vous allez créer un serveur. Prenez note du serveur. Consultez [ce didacticiel](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) pour créer une base de données en quelques minutes.

1. Se connecter à votre portail Azure.
1. Sélectionnez **créer une ressource** dans le coin supérieur gauche du volet de navigation. 
1. Sélectionnez **bases de données** , puis sélectionnez **base de données SQL**. 
1. Renseignez les informations demandées.
1. Dans le **sélectionner une Source** champ, sélectionnez **exemple (AdventureWorksLT)** pour restaurer une sauvegarde de la dernière sauvegarde AdventureWorksLT.
1. Sélectionnez **créer** pour créer votre nouvelle base de données SQL, qui est la copie restaurée de la base de données AdventureWorksLT. 


## <a name="see-also"></a>Voir aussi
[Didacticiels pour SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)
[didacticiels pour le moteur de base de données SQL Server](../relational-databases/database-engine-tutorials.md)
