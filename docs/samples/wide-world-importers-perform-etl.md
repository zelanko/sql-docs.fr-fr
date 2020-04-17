---
title: WideWorldImportersDW - Flux de travail ETL (fr) Microsoft Docs
description: Utilisez le paquet ETL avec SQL Server Integration Services (SSIS) pour migrer périodiquement les données de la base de données WideWorldImporters vers le WideWorldImportersDW.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 98ce2b9aa11b2e1381da1f16455df8a2c0d3f243
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487428"
---
# <a name="wideworldimportersdw-etl-workflow"></a>Flux de travail LARGEWorldImportersDW ETL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Utilisez le *paquet ETL WWI_Integration* pour migrer les données de la base de données WideWorldImporters vers la base de données WideWorldImportersDW au fur et à mesure que les données changent. Le paquet est exécuté périodiquement (généralement tous les jours).

Le paquet assure des performances élevées en utilisant SQL Server Integration Services pour orchestrer les opérations en vrac T-SQL (au lieu de transformations distinctes dans les services d’intégration).

Les dimensions sont chargées d’abord, puis les tables d’information sont chargées. Vous pouvez réexécuter le paquet à tout moment après une défaillance.

Le flux de travail ressemble à ceci:

 ![WideWorldImporters ETL workflow](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Le flux de travail commence par une tâche d’expression qui détermine le temps de coupure approprié. Le temps de coupure est l’heure actuelle moins quelques minutes. (Cette approche est plus robuste que de demander des données directement à l’heure actuelle.) Toutes les millisecondes sont tronquées à partir de l’époque.

Le traitement principal commence par le peuplement de la table de dimension Date. Le traitement garantit que toutes les dates pour l’année en cours ont été remplies dans le tableau.

Ensuite, une série de tâches de flux de données charge chaque dimension. Ensuite, ils chargent chaque fait.

## <a name="prerequisites"></a>Prérequis

- SQL Server 2016 (ou plus tard), avec les bases de données WideWorldImporters et WideWorldImportersDW (dans le même ou dans différents cas de SQL Server)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - Assurez-vous de créer un catalogue de services d’intégration. Pour créer un catalogue de services d’intégration, dans SQL Server Management Studio Object Explorer, cliquez à droite **sur les services d’intégration,** puis sélectionnez **Add Catalog**. Laissez les options par défaut. Vous êtes invité à activer SQLCLR et à fournir un mot de passe.


## <a name="download"></a>Téléchargement

Pour la dernière version de l’échantillon, voir [large-monde-importateurs-libération](https://go.microsoft.com/fwlink/?LinkID=800630). Téléchargez le fichier de paquet *Quotidien ETL.ispac* Integration Services.

Pour que le code source recrée la base de données de l’échantillon, voir [les importateurs du monde](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-ssis)entier .

## <a name="install"></a>Installer

1. Déployer le paquet Services d’intégration :
   1. Dans Windows Explorer, ouvrez le forfait *Daily ETL.ispac.* Cela lance le SQL Server Integration Services Deployment Wizard.
   2. Sous **Select Source**, suivez les défauts de déploiement du projet, le chemin pointant vers le paquet Daily *ETL.ispac.*
   3. Sous **Select Destination**, entrez le nom du serveur qui héberge le catalogue des services d’intégration.
   4. Sélectionnez un chemin dans le catalogue des services d’intégration, par exemple, dans un nouveau dossier nommé *WideWorldImporters*.
   5. Sélectionnez **Déployer** pour terminer l’assistant.

2. Créer un poste d’agent serveur SQL pour le processus ETL :
   1. Dans Management Studio, cliquez à droite **SQL Server Agent**, puis sélectionnez **New** > **Job**.
   2. Entrez un nom, par exemple, *WideWorldImporters ETL*.
   3. Ajoutez une **étape d’emploi** du type **SQL Server Integration Services Package**.
   4. Sélectionnez le serveur qui dispose du catalogue des services d’intégration, puis sélectionnez le forfait *ETL quotidien.*
   5. Sous **Configuration** > **Connection Managers**, assurez-vous que les connexions à la source et à la cible sont configurées correctement. La valeur par défaut est de se connecter à l’instance locale.
   6. Sélectionnez **OK** pour créer le travail.

3. Exécuter ou planifier le travail.
