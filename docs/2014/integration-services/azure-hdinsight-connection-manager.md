---
title: Gestionnaire de connexions Azure HDInsight | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2dea61640bd155e58cef2d7c8261b2ca7733bd4d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62836258"
---
# <a name="azure-hdinsight-connection-manager"></a>Gestionnaire de connexions Azure HDInsight
Le **gestionnaire de connexions Azure HDInsight** permet à un package SSIS de se connecter à un cluster Azure HDInsight.

Pour créer et configurer un **gestionnaire de connexions Azure HDInsight**, effectuez les étapes suivantes :

1. Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **AzureHDInsight**, puis cliquez sur **Ajouter**.
2. Dans l’**Éditeur du gestionnaire de connexions Azure HDInsight**, spécifiez le **nom DNS du cluster** (sans le préfixe de protocole), le **nom d’utilisateur** et le **mot de passe** du cluster HDInsight auquel se connecter.
3. Cliquez sur **OK** pour fermer la boîte de dialogue.
4. Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .
