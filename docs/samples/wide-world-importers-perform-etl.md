---
title: WideWorldImportersDW - flux de travail ETL | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36638c4cc2bda58ac277822d5c4a4ce5421ab8b4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38066527"
---
# <a name="wideworldimportersdw-etl-workflow"></a>Flux de travail WideWorldImportersDW ETL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Utilisez le *WWI_Integration* package ETL pour migrer des données à partir de la base de données WideWorldImporters vers la base de données WideWorldImportersDW en tant que les modifications de données. Le package est exécuté périodiquement (généralement quotidienne).

Le package garantit des performances élevées à l’aide de SQL Server Integration Services pour orchestrer les opérations en bloc T-SQL (au lieu de transformations distinctes dans Integration Services).

Dimensions sont chargées en premier, puis les tables de faits sont chargés. Vous pouvez réexécuter le package à tout moment après une défaillance.

Le flux de travail se présente comme suit :

 ![Flux de travail ETL de WideWorldImporters](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Le workflow démarre avec une tâche d’expression qui détermine le moment opportun de coupure. L’heure limite est l’heure actuelle moins quelques minutes. (Cette approche est plus robuste que la demande des données directement à l’heure actuelle). Les millisecondes sont tronqués à partir du moment.

Le traitement principal démarre en remplissant la table de dimension de Date. Le traitement garantit que toutes les dates pour l’année en cours ont été renseignées dans la table.

Ensuite, une série de tâches de flux de données charge chaque dimension. Ensuite, leur chargement chaque fait.

## <a name="prerequisites"></a>Prérequis

- SQL Server 2016 (ou version ultérieure), avec les bases de données WideWorldImporters et WideWorldImportersDW (dans le même ou dans différentes instances de SQL Server)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - Vérifiez que vous créez un catalogue Integration Services. Pour créer un catalogue Integration Services, dans l’Explorateur d’objets SQL Server Management Studio, avec le bouton droit **Integration Services**, puis sélectionnez **ajouter un catalogue**. Laissez les options par défaut. Vous êtes invité à activer SQLCLR et fournir un mot de passe.


## <a name="download"></a>Télécharger

Pour obtenir la dernière version de l’exemple, consultez [wide world importers libération](http://go.microsoft.com/fwlink/?LinkID=800630). Téléchargez le *ETL.ispac quotidienne* fichier de package Integration Services.

Pour le code source recréer la base de données, consultez [Wide wide world importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl).

## <a name="install"></a>Installation

1. Déployer le package Integration Services :
   1. Dans l’Explorateur Windows, ouvrez le *ETL.ispac quotidienne* package. Cette opération lance l’Assistant de déploiement de SQL Server Integration Services.
   2. Sous **sélectionner une Source**, suivez les valeurs par défaut pour le déploiement de projet, avec le chemin d’accès pointant vers le *ETL.ispac quotidienne* package.
   3. Sous **sélectionner la Destination**, entrez le nom du serveur qui héberge le catalogue Integration Services.
   4. Sélectionnez un chemin d’accès sous le catalogue Integration Services, par exemple, dans un nouveau dossier nommé *WideWorldImporters*.
   5. Sélectionnez **déployer** pour terminer l’Assistant.

2. Créer un travail de SQL Server Agent pour le processus ETL :
   1. Dans Management Studio, cliquez sur **Agent SQL Server**, puis sélectionnez **New** > **travail**.
   2. Entrez un nom, par exemple, *WideWorldImporters ETL*.
   3. Ajouter un **étape de travail** du type **Package SQL Server Integration Services**.
   4. Sélectionnez le serveur qui a le catalogue Integration Services, puis le *ETL quotidienne* package.
   5. Sous **Configuration** > **gestionnaires de connexions**, assurez-vous que les connexions à la source et cible sont configurées correctement. La valeur par défaut consiste à se connecter à l’instance locale.
   6. Sélectionnez **OK** pour créer le travail.

3. Exécuter ou planifier le travail.
