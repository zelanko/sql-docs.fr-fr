---
title: Découverte et classification des données dans SqlClient
description: Explique comment vérifier si une base de données SQL Server prend en charge la classification des données et comment accéder aux informations de classification des données au moyen d’un objet SqlDataReader.
ms.date: 06/15/2020
dev_langs:
- csharp
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: johnnypham
ms.author: v-jopha
ms.reviewer: ''
ms.openlocfilehash: 6d82bfd3c49576a35b24f5a04cdc2c03dceeb766
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081498"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>Découverte et classification des données dans SqlClient

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

[Découverte et classification des données](../../../relational-databases/security/sql-data-discovery-and-classification.md) est un ensemble de services avancés de découverte, de classification, d’étiquetage des données sensibles dans les bases de données et de création de rapports associés. SqlClient fournit une API permettant de mettre au jour les informations de découverte et de classification des données en lecture seule lorsque la source sous-jacente prend en charge la fonctionnalité. Ces informations sont accessibles par le biais de SqlDataReader.

Cet exemple d’application montre comment accéder aux propriétés de classification des données de SqlDataReader.

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**Voir aussi**  

 [Fonctionnalités de SQL Server et ADO.NET](sql-server-features-adonet.md)