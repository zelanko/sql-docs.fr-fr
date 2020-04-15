---
title: Vue d’ensemble de la migration de SQL Server Integration Services vers Azure | Microsoft Docs
description: Cet article présente les processus et les outils permettant de migrer SQL Server Integration Services vers Azure.
ms.date: 04/10/2020
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81fb9b9cb792cf350137a375e7a2e25643656b6e
ms.sourcegitcommit: 335d27d0493ddf4ffb770e13f8fe8802208d25ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "81002850"
---
# <a name="migrate-on-premises-ssis-workloads-to-ssis-in-adf"></a>Migrer des charges de travail SSIS locales vers SSIS dans ADF

Cet article liste les processus et les outils qui peuvent vous aider à migrer des charges de travail SQL Server Integration Services (SSIS) vers SSIS dans ADF.

La [vue d’ensemble de la migration](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview) présente le processus de migration de vos charges de travail ETL dans SSIS au niveau local vers SSIS dans ADF.

Le processus de migration se déroule en deux phases : l’[évaluation](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#assessment) et la [migration](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration).

## <a name="assessment"></a>Évaluation

À cette fin, vous pouvez utiliser l’Assistant Migration de données (DMA), un outil disponible en téléchargement gratuit qui peut être installé et exécuté localement. Vous pouvez créer un projet d’évaluation DMA de type Services d’intégration pour évaluer des packages SSIS par lots et identifier les problèmes de compatibilité.

Obtenez l’[Assistant Migration de base de données](https://docs.microsoft.com/sql/dma/dma-overview) et [procédez à l’évaluation des packages](https://docs.microsoft.com/sql/dma/dma-assess-ssis).

## <a name="migration"></a>Migration

Les étapes de migration des packages SSIS et des travaux de SQL Server Agent qui planifient les exécutions de packages SSIS peuvent varier selon les types de stockage des packages SSIS sources et la destination de la migration des charges de travail de base de données. Pour plus d’informations, consultez [cette page](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview#migration).

## <a name="next-steps"></a>Étapes suivantes

- [Faire migrer des packages SSIS vers une instance managée d’Azure SQL Database](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance).
- [Migrez les travaux SSIS vers Azure Data Factory (ADF) avec SQL Server Management Studio (SSMS)](https://docs.microsoft.com/azure/data-factory/how-to-migrate-ssis-job-ssms).
