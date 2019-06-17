---
title: Données des rapports
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services-2014, sql-server-2014
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 8c0a6ef25f33b5396ecea36edfd57ac3c42e8f5b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721408"
---
# <a name="report-data-in-sql-server-reporting-services-ssrs"></a>Données des rapports dans SQL Server Reporting Services (SSRS)

  Les données de rapport peuvent provenir de plusieurs sources de données de votre organisation. Votre première étape lors de la conception d'un rapport consiste à créer des sources de données et des datasets qui représentent les données de rapport sous-jacentes. Chaque source de données inclut des informations de connexion de données. Chaque dataset inclut une commande de requête qui définit le jeu de champs à utiliser comme données d'une source de données. Pour visualiser des données de chaque dataset, ajoutez une région de données, telle qu'une table, une matrice, un graphique ou une carte. Lorsque le rapport est traité, les requêtes s'exécutent sur la source de données, et chaque région de données s'étend autant que nécessaire pour afficher les résultats de la requête pour le dataset.  
  
##  <a name="BkMk_ReportDataTerms"></a> Termes

 Si vous n’êtes pas familiarisé avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] concepts, passez en revue les termes suivants dans [Concepts de Reporting Services &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md): *connexion de données*, *des données incorporées sources*, *sources de données partagées*, *datasets incorporés*, *datasets partagés*, *requêtes de dataset* , *parties de rapport*, et *alertes de données*.  
  
##  <a name="BkMk_ReportDataTips"></a> Conseils pour spécifier les données de rapport

 Utilisez les informations suivantes pour concevoir votre stratégie de données de rapport.  
  
- **Sources de données** Les sources de données peuvent être publiées et gérées indépendamment des rapports sur un serveur de rapports ou un site SharePoint. Pour chaque source de données, vous ou le propriétaire de la base de données pouvez gérer les informations de connexion dans un seul emplacement. Les informations d'identification de la source de données sont stockées de manière sécurisée sur le serveur de rapports ; n'incluez pas de mots de passe dans la chaîne de connexion. Vous pouvez rediriger une source de données d'un serveur de test vers un serveur de production. Vous pouvez désactiver une source de données pour interrompre tous les rapports qui l'utilisent. Pour obtenir la liste des sources de données prises en charge, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
- **Datasets** Les datasets peuvent être publiés et gérés indépendamment des rapports ou des sources de données partagées desquels ils dépendent. Vous ou le propriétaire de la base de données pouvez fournir des requêtes optimisées pour les auteurs de rapport à utiliser. Lorsque vous modifiez la requête, tous les rapports qui se servent des datasets partagés utilisent la requête mise à jour. Vous pouvez autoriser la mise en cache du dataset pour améliorer les performances. Vous pouvez planifier la mise en cache de requête à un moment donné ou utiliser une planification partagée.  
  
- **Données utilisées par les parties de rapports** Les parties de rapport peuvent incluent les données dont elles dépendent. Pour plus d’informations sur les parties de rapport, consultez [Parties de rapport dans le Concepteur de rapports &#40;SSRS&#41;](../report-design/report-parts-in-report-designer-ssrs.md).  
  
- **Filtrer les données** Les données de rapport peuvent être filtrées dans la requête ou dans le rapport. Vous pouvez utiliser des datasets et interroger des variables pour créer des paramètres en cascade et fournir à l'utilisateur la possibilité de limiter les choix parmi des milliers de sélections à un nombre plus gérable. Vous pouvez filtrer les données dans une table ou un graphique en fonction des valeurs des paramètres ou d'autres valeurs que vous spécifiez.  
  
- **Paramètres** Les commandes de requête de datasets qui incluent des variables de requêtes créent automatiquement les paramètres de rapport correspondants. Vous pouvez également créer des paramètres manuellement. Lorsque vous affichez un rapport, la barre d'outils Rapport affiche les paramètres. Les utilisateurs peuvent sélectionner des valeurs pour contrôler l'apparence des données de rapport ou du rapport. Pour personnaliser les données du rapport pour un public donné, vous pouvez créer des ensembles de paramètres de rapport avec différentes valeurs par défaut liées à la même définition de rapport ou utiliser le champ prédéfini `UserID`. Pour plus d’informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) et [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
- **Alertes de données** Après la publication d'un rapport, vous pouvez créer des alertes sur des données de rapport et recevoir des messages électroniques lorsqu'elle satisfait aux règles que vous spécifiez.  
  
- **Groupe et données agrégées** Les données de rapport peuvent être regroupées et agrégées dans la requête ou dans le rapport. Si vous agrégez des valeurs dans la requête, vous pouvez continuer à combiner des valeurs dans le rapport dans des limites de ce qui est explicite.  Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) et [Fonction d’agrégation &#40;Générateur de rapports et SSRS&#41;](../report-design/report-builder-functions-aggregate-function.md).  
  
- **Trier des données** Les données de rapport peuvent être triées dans la requête ou dans le rapport. Dans les tables, vous pouvez également ajouter un bouton de tri interactif pour permettre à l'utilisateur de contrôler l'ordre de tri.  
  
- **Données basées sur des expressions** Comme la plupart des propriétés de rapport peuvent être basées sur des expressions, et que les expressions peuvent inclure des références à des champs de dataset et à des paramètres de rapport, vous pouvez écrire des expressions puissantes pour contrôler les données et l’apparence du rapport. Vous pouvez fournir à l'utilisateur la possibilité de contrôler les données qu'il consulte en définissant des paramètres.  
  
- **Afficher les données d'un dataset** Les données d'un dataset sont généralement affichées sur une ou plusieurs régions de données, par exemple, une table et un graphique.  
  
- **Afficher les données de plusieurs datasets**  Vous pouvez écrire des expressions dans une région de données basée sur un dataset qui recherche des valeurs ou des agrégats dans d'autres datasets. Vous pouvez inclure des sous-rapports dans une table selon un dataset pour afficher les données d'une source de données différente.  
  
## <a name="data-connections-data-sources-and-datasets"></a>Connexions de données, sources de données et datasets

 Utilisez la liste suivante pour définir les sources de données d'un rapport.  
  
- Envisagez d'utiliser, ou non, les sources de données et les datasets incorporés ou partagés. Collaborez avec les propriétaires des sources de données pour implémenter et utiliser l'authentification et la technologie d'autorisation appropriée pour votre organisation.  
  
- Comprenez l'architecture de la couche de données logicielle de votre organisation et les problèmes potentiels résultant des types de données. Comprenez comment les extensions de données et les extensions pour le traitement des données peuvent affecter les résultats de la requête. Les types de données diffèrent entre la source de données, les fournisseurs de données et les types de données stockés dans le fichier de définition de rapport (.rdl).  
  
- Comprenez les architectures et les outils client/serveur de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Par exemple, dans le Concepteur de rapports, créez des rapports sur un ordinateur client qui utilise les types de sources de données intégrés. Lorsque vous publiez un rapport, les types de source de données doivent être pris en charge sur le serveur de rapports ou sur le site SharePoint.  Pour plus d’informations, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
- Les sources de données et les datasets sont créés dans un rapport et publiés sur un serveur de rapports ou un site SharePoint à partir d'un outil de création client. Les sources de données peuvent être créées directement sur le serveur de rapports. Une fois qu'ils sont publiés, vous pouvez configurer les informations d'identification et d'autres propriétés sur le serveur de rapports. Pour plus d’informations, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) et [outils de Reporting Services](../tools/reporting-services-tools.md).  
  
- Les sources de données que vous pouvez utiliser dépendent des extensions de données de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui sont installées. La prise en charge des sources de données peut être différente selon l'outil de création client, la version du serveur de rapports et la plateforme de serveur de rapports. Pour plus d’informations, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
- Les informations d'identification de la source de données varient selon le type de source de données et selon que les rapports sont affichés, ou non, sur votre serveur client, sur votre serveur de rapports ou sur un site SharePoint. Pour plus d’informations, consultez [Définir les autorisations sur les éléments de serveur de rapports sur un site SharePoint &#40;Reporting Services en mode intégré SharePoint&#41;](../security/set-permissions-for-report-server-items-on-a-sharepoint-site.md), [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](../../integration-services/connection-manager/data-sources.md) et les informations d’identification propres à chaque outil dans [Outils de Reporting Services](../tools/reporting-services-tools.md).  
  
## <a name="related-tasks"></a>Tâches associées

 Les tâches liées à la création des connexions de données, l'ajout de données provenant de sources externes, de datasets et de requêtes.  
  
|||  
|-|-|  
|**Tâches courantes**|**Liens**|  
|Créer des connexions de données|[Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)|  
|Créer des datasets et des requêtes|[Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)|  
|Gérer les sources de données après leur publication|[Gérer des sources de données de rapports](manage-report-data-sources.md)|  
|Gérer des datasets partagés après leur publication|[Gérer des datasets partagés](manage-shared-datasets.md)|  
|Créer et gérer des alertes de données|[Alertes de données Reporting Services](../tutorial-creating-a-basic-table-report-report-builder.md)|  
|Mettre en cache un dataset partagé|[Mettre en cache les datasets partagés &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md)|  
|Planifier un dataset partagé pour précharger le cache|[Planifications](../subscriptions/schedules.md)|  
|Ajouter une extension de données|[Mise en œuvre d’une extension pour le traitement des données](../extensions/data-processing/implementing-a-data-processing-extension.md)|