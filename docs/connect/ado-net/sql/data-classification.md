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
ms.openlocfilehash: b53e71c4c302145af14c1f2e37f30fe0e3c8f8e2
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725720"
---
# <a name="data-discovery-and-classification-in-sqlclient"></a>Découverte et classification des données dans SqlClient

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

[Découverte et classification des données](../../../relational-databases/security/sql-data-discovery-and-classification.md?view=sql-server-2017) est un ensemble de services avancés de découverte, de classification, d’étiquetage des données sensibles dans les bases de données et de création de rapports associés. SqlClient fournit une API permettant de mettre au jour les informations de découverte et de classification des données en lecture seule lorsque la source sous-jacente prend en charge la fonctionnalité. Ces informations sont accessibles par le biais de SqlDataReader.

Cet exemple d’application montre comment accéder aux propriétés de classification des données de SqlDataReader.

[!code-csharp [SqlDataReader_DataDiscoveryAndClassification#1](~/../sqlclient/doc/samples/SqlDataReader_DataDiscoveryAndClassification.cs#1)]

**Voir aussi**  

 [Fonctionnalités de SQL Server et ADO.NET](sql-server-features-adonet.md)