---
description: Appliquer des règles de qualité des données à la source de données
title: Appliquer des règles de qualité des données à la source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58e6e75f520bcd966cf2b1ae8e2edbc0f7a568f7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484415"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Appliquer des règles de qualité des données à la source de données

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Vous pouvez utiliser Data Quality (DQS) Services pour corriger les données dans le flux de données du package en connectant la transformation de nettoyage DQS à la source de données. Pour plus d’informations sur DQS, consultez [Concepts Data Quality Services](../../../data-quality-services/data-quality-services-concepts.md). Pour plus d’informations sur la transformation, consultez [Transformation de nettoyage DQS](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Lorsque vous traitez des données avec la transformation de nettoyage DQS, un projet de qualité des données est créé sur le serveur de qualité des données. Vous utilisez le client de qualité des données pour gérer le projet. Pour plus d’informations, consultez [Ouvrir, déverrouiller, renommer et supprimer un projet de qualité des données](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Pour corriger les données dans le flux de données  
  
1.  Créer un package.  
  
2.  Ajoutez et configurez la transformation de nettoyage DQS. Pour plus d’informations, consultez [Éditeur de transformation de nettoyage DQS (boîte de dialogue)](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Connectez la transformation de nettoyage DQS à une source de données.  
  
  
