---
title: Base de données exemple WideWorldImporters OLAP - installer et configurer - SQL | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 859945ae5f255327ff6dc12b58b126849db66ba8
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39551950"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>WideWorldImportersDW Installation et configuration
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Instructions d’installation et de configuration pour la base de données WideWorldImportersDW.

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (ou version ultérieure) ou [Azure SQL Database](https://azure.microsoft.com/services/sql-database/). Pour utiliser la version complète de l’exemple, utilisez SQL Server Evaluation/développeur/Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Pour de meilleurs résultats, utilisez la version de juin 2016 ou version ultérieure.

## <a name="download"></a>Télécharger

La dernière version de l’exemple :

[wide-world-importers-release](http://go.microsoft.com/fwlink/?LinkID=800630)

Télécharger l’exemple WideWorldImportersDW base de données sauvegarde/fichier bacpac qui correspond à votre édition de SQL Server ou de la base de données SQL Azure.

Code source pour recréer la base de données est disponible à partir de l’emplacement suivant. Notez que le remplissage des données est basé sur ETL à partir de la base de données OLTP (WideWorldImporters) :

[wide-world-importers-source](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

## <a name="install"></a>Installation


### <a name="sql-server"></a>SQL Server

Pour restaurer une sauvegarde à une instance de SQL Server, vous pouvez utiliser Management Studio.

1. Ouvrez SQL Server Management Studio et connectez-vous à l’instance de SQL Server cible.
2. Avec le bouton droit sur le **bases de données** nœud, puis sélectionnez **Restore Database**.
3. Sélectionnez **appareil** , puis cliquez sur le bouton **...**
4. Dans la boîte de dialogue **sélectionner les unités de sauvegarde**, cliquez sur **ajouter**, accédez à la sauvegarde de base de données dans le système de fichiers du serveur et sélectionnez la sauvegarde. Cliquez sur **OK**.
5. Si nécessaire, modifiez l’emplacement cible pour les données et fichiers journaux, dans le **fichiers** volet. Notez qu’il est recommandé de placer des données et fichiers journaux sur des lecteurs différents.
6. Cliquez sur **OK**. Ceci lancera la restauration de base de données. Une fois terminé, vous aurez la base de données WideWorldImporters installés sur votre instance de SQL Server.

### <a name="azure-sql-database"></a>Azure SQL Database

Pour importer un fichier bacpac dans une base de données SQL, vous pouvez utiliser Management Studio.

1. (facultatif) Si vous n’avez pas encore d’un serveur SQL Server dans Azure, accédez à la [Azure portal](https://portal.azure.com/) et créer une base de données SQL. En cours de créer une base de données, vous allez créer un serveur. Prenez note du serveur.
   - Consultez [ce didacticiel](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) pour créer une base de données en quelques minutes
2. Ouvrez SQL Server Management Studio et connectez-vous à votre serveur dans Azure.
3. Avec le bouton droit sur le **bases de données** nœud, puis sélectionnez **importer une Application de couche données**.
4. Dans le **importer les paramètres** sélectionnez **importer à partir du disque local** et sélectionnez le fichier bacpac de la base de données à partir de votre système de fichiers.
5. Sous **les paramètres de base de données** modifier le nom de la base de données à *WideWorldImportersDW* et sélectionnez l’objectif d’édition et le service cible à utiliser.
6. Cliquez sur **suivant** et **Terminer** pour lancer le déploiement. Il prendra quelques minutes pour terminer. Lorsque vous spécifiez un objectif de service inférieur à S2 peut prendre plus de temps.

## <a name="configuration"></a>Configuration

[S’applique à SQL Server 2016 (et versions ultérieures) d’évaluation/Developer/Enterprise Edition]

La base de données peut se servir de PolyBase pour les fichiers de requête dans Hadoop ou Azure blob storage. Toutefois, cette fonctionnalité n’est pas installée par défaut avec SQL Server : vous devez le sélectionner lors de l’installation de SQL Server. Par conséquent, une étape après l’installation est requise.

1. Dans SQL Server Management Studio, vous connecter à la base de données WideWorldImportersDW et ouvrez une nouvelle fenêtre de requête.
2. Exécutez la commande T-SQL suivante pour activer l’utilisation de PolyBase dans la base de données :

   Exécutez [Application]. [Configuration_ApplyPolyBase]
