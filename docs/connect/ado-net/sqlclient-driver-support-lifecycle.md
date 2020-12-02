---
title: Cycle de vie de prise en charge du pilote SqlClient
description: Page contenant des informations sur le cycle de vie du support technique.
ms.date: 11/19/2020
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-jizho2
ms.openlocfilehash: 30155a584de4e22692601a1dcf9551a67d4f580f
ms.sourcegitcommit: 4c3949f620d09529658a2172d00bfe37aeb1a387
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95011787"
---
# <a name="sqlclient-driver-support-lifecycle"></a>Cycle de vie de prise en charge du pilote SqlClient

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

La bibliothèque Microsoft.Data.SqlClient suit la dernière stratégie de prise en charge de .NET Core pour toutes les versions.

[Afficher la stratégie de prise en charge de .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

## <a name="microsoftdatasqlclient-release-cadence"></a>Cadence de publication de Microsoft.Data.SqlClient

Les nouvelles versions stables (GA) seront publiées tous les six mois sur une cadence normale à partir de la version 1.2, avec en plus de 2 à 3 préversions entre elles. Les versions avec prise en charge à long terme (LTS) seront choisies par les parties prenantes et les responsables de maintenance en fonction de quelques qualifications et de la réponse des clients.

### <a name="release-life-cycles"></a>Cycles de vie des versions

| Version | Date de publication officielle | Dernière version du correctif | Date de publication du correctif | Niveau de prise en charge  | Fin du support |
| -- | -- | -- | -- | -- | -- |
| 2.1 | 19 novembre 2020 | 2.1.0 | 19 novembre 2020 | Actuel | |
| 2.0 | 16 juin 2020 | 2.0.1 | 25 août 2020 | Actuel | |
| 1.1 | 20 novembre 2019 | 1.1.3 | 15 mai 2020 | LTS | 21 novembre 2022 |
| 1.0 | 28 août 2019 | 1.0.19269.1 | 26 septembre 2019 | Actuel | 20 février 2020 |

### <a name="long-term-support-lts-releases"></a>Versions avec prise en charge à long terme (LTS)

Les versions LTS sont prises en charge pendant trois ans après la version initiale.

### <a name="current-releases"></a>Versions actuelles

Les versions actuelles sont prises en charge pendant trois mois après la publication d’une version actuelle ou LTS postérieure.

## <a name="sql-version-compatibility-with-microsoftdatasqlclient"></a>Compatibilité des versions SQL avec Microsoft.Data.SqlClient

|Version de la base de données&nbsp;&#8594;<br />Version du pilote &#8595;|Azure SQL Database|Azure Synapse Analytics|Azure SQL Managed Instance|SQL Server 2019|SQL Server 2017|SQL Server 2016|SQL Server 2014|SQL Server 2012|
|---|---|---|---|---|---|---|---|---|
|2.1|Oui|Oui|Oui|Oui|Oui|Oui|Oui|Oui|
|2.0|Oui|Oui|Oui|Oui|Oui|Oui|Oui|Oui|
|1.1|Oui|Oui|Oui|Oui|Oui|Oui|Oui|Oui|
|1.0|Oui|Oui|Oui|Oui|Oui|Oui|Oui|Oui|
