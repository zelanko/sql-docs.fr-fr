---
title: Mise en correspondance de la qualité des données dans le Complément MDS pour Excel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: be78d051-0d56-46d3-bb89-327e218dadd6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 139bda733610f7f4ac54b2d438ba73b29831427c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62764599"
---
# <a name="data-quality-matching-in-the-mds-add-in-for-excel"></a>Mise en correspondance de la qualité des données dans le complément MDS pour Excel
  Au fil du temps, vous souhaiterez ajouter des données au référentiel MDS. Avant d’ajouter des données, il peut être utile de comparer les nouvelles données aux données qui sont déjà managées dans MDS pour s’assurer de ne pas ajouter de données dupliquées ou incorrectes.  
  
 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] utilise la fonctionnalité Data Quality Services (DQS) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour faire correspondre les données similaires. Lorsque vous utilisez la fonctionnalité de correspondance du complément, les enregistrements similaires sont regroupés et un score qui représente la précision du résultat est affiché. Pour plus d’informations sur la fonctionnalité de correspondance fournie par DQS, consultez [Correspondance de données](../../data-quality-services/data-matching.md).  
  
## <a name="workflow-for-data-quality-matching"></a>Flux de travail pour la correspondance de la qualité des données  
 Quand vous utilisez DQS avec MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], utilisez le flux de travail suivant :  
  
1.  Récupérez une liste de données managées MDS et combinez-la avec une liste non gérée dans MDS. Pour plus d’informations, consultez [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).  
  
2.  Utilisez la base de connaissances DQS pour comparer les données dans la liste combinée. Pour plus d’informations, consultez [Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](match-similar-data-mds-add-in-for-excel.md).  
  
3.  Pour plus de détails sur les similitudes identifiées par DQS, affichez les colonnes de détail.  
  
4.  Explorez les résultats et déterminez les données qui doivent être ajoutées au référentiel MDS et celles qui sont dupliquées.  
  
5.  Publiez les données nouvelles et/ou mises à jour dans le référentiel MDS.  
  
## <a name="knowledge-bases"></a>Bases de connaissances  
 Les résultats correspondants fournis dans le complément sont basés sur une base de connaissances DQS.  
  
-   La base de connaissances par défaut (DQS Data) est créée lors de l'installation de DQS. Si vous choisissez d'utiliser la base de connaissances par défaut (sans ajouter de stratégie de correspondance à la base de connaissances par défaut dans le client de qualité des données), vous devez mapper les colonnes dans la feuille de calcul aux domaines de la base de connaissances, puis attribuer une valeur de pondération aux domaines que vous choisissez.  
  
-   Vous pouvez utiliser le client de qualité des données pour créer une nouvelle base de connaissances avec une stratégie de correspondance, ou pour ajouter une stratégie de correspondance à la base de connaissances par défaut. Dans ce cas, les valeurs de pondération sont déterminées par la stratégie correspondante que vous avez déjà créée et vous devez uniquement mapper les colonnes aux domaines. Pour plus d’informations, consultez [Créer une stratégie de correspondance](../../data-quality-services/create-a-matching-policy.md).  
  
 Pour plus d’informations sur les bases de connaissances, consultez [Bases de connaissances et domaines DQS](../../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Combinez les données externes avec les données managées MDS en préparation pour les comparer.|[Combiner des données &#40;Complément MDS pour Excel&#41;](combine-data-mds-add-in-for-excel.md)|  
|Utilisez la base de connaissances DQS pour rechercher des similitudes dans vos données.|[Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](match-similar-data-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Publication de données &#40;complément MDS pour Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Correspondance de données](../../data-quality-services/data-matching.md)  
  
  
