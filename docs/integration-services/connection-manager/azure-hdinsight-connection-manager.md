---
description: Gestionnaire de connexions Azure HDInsight
title: Gestionnaire de connexions Azure HDInsight | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPHDICM.F1
- SQL14.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 29d01bd9-8b38-43b1-b937-67f8aea57c0f
author: Lingxi-Li
ms.author: lingxl
ms.openlocfilehash: 6acb9fec83da610246001df5bc68591ecab1a225
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478011"
---
# <a name="azure-hdinsight-connection-manager"></a>Gestionnaire de connexions Azure HDInsight

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Le **gestionnaire de connexions Azure HDInsight** permet à un package SSIS de se connecter à un cluster Azure HDInsight.

Le **gestionnaire de connexions Azure HDInsight** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Pour créer et configurer un **gestionnaire de connexions Azure HDInsight**, effectuez les étapes suivantes :

1. Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **AzureHDInsight**, puis cliquez sur **Ajouter**.
2. Dans l’**Éditeur du gestionnaire de connexions Azure HDInsight**, spécifiez le **nom DNS du cluster** (sans le préfixe de protocole), le **nom d’utilisateur** et le **mot de passe** du cluster HDInsight auquel se connecter.
3. Cliquez sur **OK** pour fermer la boîte de dialogue.
4. Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .
