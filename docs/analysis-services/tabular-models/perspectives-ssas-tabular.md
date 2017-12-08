---
title: Perspectives (SSAS tabulaire) | Documents Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 36e28c1211017a46a66ce7c7ef519eb887248c8f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="perspectives"></a>Perspectives
  Dans les modèles tabulaires, les perspectives définissent des sous-ensembles visualisables d'un modèle et des points de vue du modèle focalisés sur un domaine d'activité ou sur une application.  
  
##  <a name="bkmk_understanding"></a> Avantages  
 L'exploration des modèles tabulaires peut s'avérer très complexe pour les utilisateurs. Un modèle unique peut représenter le contenu d'un entrepôt de données complet avec de nombreuses tables, mesures et dimensions. Une telle complexité peut dérouter les utilisateurs qui n'ont besoin d'interagir qu'avec une petite partie du modèle afin de répondre à leurs besoins en termes de décisionnel et de rapports.  
  
 Dans une perspective, les tables, les colonnes et les mesures (dont les KPI) sont définis en tant qu'objets de champ. Vous pouvez sélectionner les champs visibles pour chaque perspective. Par exemple, un modèle peut contenir des données relatives au produit et aux ventes, ainsi que des données financières, des données géographiques et des données relatives aux employés. Si le service commercial a sans doute besoin des données relatives aux produits, aux ventes et aux promotions, ainsi que des données géographiques, il est peut probable qu'il s'intéresse aux données des employés et aux données financières. De même, le service des ressources humaines ne s'intéresse pas aux données relatives aux ventes et aux promotions, ni aux données géographiques.  
  
 Lorsqu'un utilisateur se connecte à un modèle (comme une source de données) avec des perspectives définies, il peut sélectionner la perspective qu'il souhaite utiliser. Par exemple, lors d'une connexion à une source de données de modèle dans Excel, les utilisateurs RH peuvent sélectionner la perspective Ressources Humaines sur la page Sélectionner des tables et des vues de l'Assistant Connexion de données. Seuls les champs (tables, colonnes et mesures) définis pour la perspective Ressources Humaines seront visibles dans la liste de champs du tableau croisé dynamique.  
  
 Les perspectives ne sont pas censées servir de mécanisme de sécurité, mais elles constituent plutôt un outil qui optimise l'expérience de l'utilisateur. L'intégralité de la sécurité d'une perspective donnée est héritée du modèle sous-jacent. Les perspectives ne peuvent pas donner accès à des objets de modèle auxquels un utilisateur n'a pas déjà accès. La sécurité de la base de données model doit d'abord être résolue, avant que l'utilisateur puisse accéder aux objets du modèle par le biais d'une perspective. Les rôles de sécurité peuvent permettre de sécuriser les métadonnées et les données de modèle. Pour plus d’informations, consultez [rôles](../../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
##  <a name="bkmk_testpersp"></a> Testing perspectives  
 Lors de la création d'un modèle, vous pouvez utiliser la fonctionnalité Analyser dans Excel dans le générateur de modèles afin de tester l'efficacité des perspectives que vous avez définies. Dans le menu **Modèle** du générateur de modèles, lorsque vous cliquez sur **Analyser dans Excel**, avant qu'Excel ne s'ouvre, la boîte de dialogue **Choisir les informations d'identification et la perspective** s'affiche. Dans cette boîte de dialogue, vous pouvez spécifier le nom d'utilisateur actuel, un utilisateur différent, un rôle et une perspective que vous utiliserez pour vous connecter à la base de données model de l'espace de travail comme source de données et afficher les données.  
  
##  <a name="bkmk_related_tasks"></a> Related tasks  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Créer et gérer des perspectives](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)|Décrit comment créer et gérer des perspectives à l'aide de la boîte de dialogue Perspectives dans le générateur de modèles.|  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Hierarchies](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  
