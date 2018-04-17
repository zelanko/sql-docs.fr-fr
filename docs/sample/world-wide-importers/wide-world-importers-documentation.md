---
title: Documentation de Wide World Importers | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17cabd9d-cb2f-436c-ad9c-ce02225808b7
caps.latest.revision: 3
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: 99d3bf3913b620a34e284b8277e4c639ba20727a
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2018
---
# <a name="wide-world-importers-documentation"></a>Documentation de Wide World Importers
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Wide World Importers est la nouvelle base de données pour SQL Server 2016 et base de données SQL Azure. Il illustre les fonctionnalités principales de SQL Server 2016 et base de données SQL Azure, pour le traitement des transactions (OLTP), entrepôt de données et les charges de travail analytique (OLAP), ainsi que les transactions hybride et les charges de travail (HTAP) de traitement analytique.

## <a name="about-this-sample"></a>Sur cet exemple

Wide World Importers est un exemple de base de données complète qui illustre la conception de base de données et illustre comment les fonctionnalités de SQL Server peuvent être exploitées dans une application.

Notez que l’exemple est destiné à être représentatif d’une base de données classique. Il n’inclut pas toutes les fonctionnalités de SQL Server. La conception de la base de données suit un ensemble commun de normes, mais il existe plusieurs façons une peut créer une base de données.

**Dernière version**: [wide world importers version](http://go.microsoft.com/fwlink/?LinkID=800630)

**Code source pour l’exemple**: [sein wide world importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers).

**Commentaires**: envoyez à [ sqlserversamples@microsoft.com ](mailto:sqlserversamples@microsoft.com).

La documentation de l’exemple est organisée comme suit :

## <a name="overview"></a>Vue d'ensemble

Vue d’ensemble de la société exemple Wide World Importers et les flux de travail traités par l’exemple.

## <a name="main-oltp-database-wideworldimporters"></a>OLTP principale de base de données WideWorldImporters

Instructions pour l’installation et la configuration des principaux de base de données WideWorldImporters est utilisé pour OLTP (traitement transactionnel - OnLine Transaction Processing) et l’analytique opérationnelle (HTAP - hybride de traitement transactionnel/analytique).

Description des schémas et des tables utilisées dans la base de données WideWorldImporters.  

Décrit comment WideWorldImporters tire parti des fonctionnalités de SQL Server core.

Exemples de requêtes pour la base de données WideWorldImporters.

## <a name="data-warehousing-and-analytics-database-wideworldimportersdw"></a>Entrepôt de données et WideWorldImportersDW de base de données Analytique

Instructions pour l’installation et la configuration de OLAP WideWorldImportersDW de base de données.

Description des schémas et des tables utilisées dans la base de données WideWorldImportersDW, qui est la base de données pour l’entrepôt de données et le traitement analytique (OLAP).

Flux de travail pour le processus ETL (Extract, Transform, Load) qui migre les données à partir de la base de données transactionnelle WideWorldImporters vers l’entrepôt de données WideWorldImportersDW.

Décrit comment le WideWorldImportersDW tire parti des fonctionnalités de SQL Server pour le traitement d’analytique.

Exemples de requêtes analytique tirant parti de la base de données WideWorldImportersDW.

## <a name="data-generation"></a>Génération de données

Décrit comment les autres données peuvent être générées dans la base de données, par exemple l’insertion des ventes et de fournisseur de données jusqu'à la date actuelle.
