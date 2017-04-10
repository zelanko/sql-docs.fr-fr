---
title: "Transformation de nettoyage DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "correction des données"
  - "corriger les données"
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# Transformation de nettoyage DQS
  La transformation de nettoyage DQS utilise les services Data Quality Services (DQS) pour corriger des données provenant d'une source de données connectée en appliquant des règles approuvées créées pour la source de données connectée ou une source de données similaire. Pour plus d'informations sur les règles de correction des données, consultez [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md). Pour plus d'informations sur DQS, consultez [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).  
  
 Pour déterminer si les données doivent être corrigée, la transformation de nettoyage DQS traite les données d'une colonne d'entrée lorsque les conditions suivantes sont remplies :  
  
-   La colonne est sélectionnée pour la correction des données.  
  
-   Le type de données de la colonne est pris en charge pour la correction des données.  
  
-   La colonne est mappée à un domaine dont le type de données est compatible.  
  
 La transformation inclut également une sortie d'erreur que vous configurez pour gérer les erreurs au niveau des lignes. Pour configurer la sortie d'erreur, utilisez l' **Éditeur de transformation de nettoyage DQS**.  
  
 Vous pouvez inclure la [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) dans le flux de données pour identifier les lignes de données susceptibles d'être en double.  
  
## Projets de qualité des données et valeurs  
 Lorsque vous traitez des données avec la transformation de nettoyage DQS, un projet de nettoyage est créé sur le serveur de qualité des données. Vous utilisez le client de qualité des données pour gérer le projet. En outre, vous pouvez utiliser le client de qualité des données pour importer les valeurs du projet dans un domaine de base de connaissances DQS. Vous pouvez importer les valeurs uniquement vers un domaine (ou un domaine lié) configuré pour être utilisé par la transformation de nettoyage DQS.  
  
## Tâches associées  
  
-   [Ouvrir des projets Integration Services dans Data Quality Client](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Import Cleansing Project Values into a Domain](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [Appliquer des règles de qualité des données à la source de données](../../../integration-services/data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
## Contenu connexe  
  
-   [Ouvrir, déverrouiller, renommer et supprimer un projet de qualité des données](https://msdn.microsoft.com/library/hh510417.aspx)  
  
-   Article [Nettoyage de données complexes à l'aide des domaines composites](http://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx), sur social.technet.microsoft.com.  
  
  