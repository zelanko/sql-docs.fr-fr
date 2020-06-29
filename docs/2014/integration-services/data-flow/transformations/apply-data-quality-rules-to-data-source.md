---
title: Appliquer des règles de qualité des données à la source de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d59e6fb5ffb752b3346d40740e0b841bf574344e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431036"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Appliquer des règles de qualité des données à la source de données
  Vous pouvez utiliser Data Quality (DQS) Services pour corriger les données dans le flux de données du package en connectant la transformation de nettoyage DQS à la source de données. Pour plus d’informations sur DQS, consultez [Concepts Data Quality Services](../../../data-quality-services/data-quality-services-concepts.md). Pour plus d’informations sur la transformation, consultez [Transformation de nettoyage DQS](dqs-cleansing-transformation.md).  
  
 Lorsque vous traitez des données avec la transformation de nettoyage DQS, un projet de qualité des données est créé sur le serveur de qualité des données. Vous utilisez le client de qualité des données pour gérer le projet. Pour plus d’informations, consultez [Gérer &#40;ouvrir, déverrouiller, renommer et supprimer&#41; un projet de qualité des données](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Pour corriger les données dans le flux de données  
  
1.  Créer un package.  
  
2.  Ajoutez et configurez la transformation de nettoyage DQS. Pour plus d’informations, consultez [Éditeur de transformation de nettoyage DQS (boîte de dialogue)](../../dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Connectez la transformation de nettoyage DQS à une source de données.  
  
  
