---
title: Transformations Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transformations [Integration Services], listed
- transformations [Integration Services], types
- transformations [Integration Services]
- data flow [Integration Services], transformations
- business intelligence transformations [Integration Services]
- join transformations
- split transformations [Integration Services]
- custom transformations [Integration Services]
- row transformations [Integration Services]
- rowset transformations [Integration Services]
ms.assetid: c70c4f6e-82dd-4948-b923-fd5193f67f7e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b283f179a6d9ad79e90e4abdfc2e5af0c199d4dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900278"
---
# <a name="integration-services-transformations"></a>Transformations Integration Services
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Les transformations sont les composants du flux de données d’un package qui agrègent, fusionnent, distribuent et modifient des données. Les transformations peuvent également effectuer des opérations de recherche et générer des échantillons de dataset. Cette section décrit les transformations incluses dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] et explique leur fonctionnement.  
  
## <a name="business-intelligence-transformations"></a>Transformations Business Intelligence  
 Les transformations suivantes effectuent des opérations décisionnelles telles que le nettoyage de données, l'exploration de texte et l'exécution de requêtes de prédiction d'exploration de données.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation de dimension à variation lente](slowly-changing-dimension-transformation.md)|Transformation qui configure la mise à jour d'une dimension à variation lente.|  
|[Transformation de regroupement probable](fuzzy-grouping-transformation.md)|Transformation qui normalise les valeurs en données de colonne.|  
|[Transformation de recherche floue](lookup-transformation.md)|Transformation qui recherche des valeurs dans une table de référence au moyen d'une correspondance approximative.|  
|[Transformation d'extraction de terme](term-extraction-transformation.md)|Transformation qui extrait des termes à partir du texte.|  
|[Transformation de recherche de terme](term-lookup-transformation.md)|Transformation qui recherche des termes dans une table de référence et compte les termes extraits à partir du texte.|  
|[Transformation de requête d’exploration de données](data-mining-query-transformation.md)|Transformation qui exécute des requêtes de prédictions d'exploration de données.|  
|[Transformation de nettoyage DQS](dqs-cleansing-transformation.md)|Transformation qui corrige des données d'une source de données connectée en appliquant des règles créées pour la source de données.|  
  
## <a name="row-transformations"></a>Transformations de lignes  
 Les transformations suivantes mettent à jour les valeurs de colonnes et créent de nouvelles colonnes. La transformation est appliquée à chaque ligne de l'entrée de transformation.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation de la table de caractères](character-map-transformation.md)|Transformation qui applique des fonctions de chaîne à des données de caractères.|  
|[Transformation Copie de colonnes](copy-column-transformation.md)|Transformation qui ajoute des copies de colonnes d'entrée à la sortie de transformation.|  
|[Transformation de conversion de données](data-conversion-transformation.md)|Transformation qui convertit le type de données d'une colonne en un type de données différent.|  
|[Transformation de colonne dérivée](derived-column-transformation.md)|Transformation qui remplit des colonnes avec les résultats d'expressions.|  
|[Transformation d'exportation de colonne](export-column-transformation.md)|Transformation qui insère des données dans un fichier à partir d'un flux de données.|  
|[Transformation d'importation de colonne](import-column-transformation.md)|Transformation qui lit des données à partir d'un fichier et les ajoute à un flux de données.|  
|[Composant Script](script-component.md)|Transformation qui utilise un script pour extraire, transformer ou charger des données.|  
|[Transformation de commande OLE DB](ole-db-command-transformation.md)|Transformation qui exécute des commandes SQL pour chaque ligne d'un flux de données.|  
  
## <a name="rowset-transformations"></a>Transformations d'ensemble de lignes  
 Les transformations suivantes créent des ensembles de lignes. L'ensemble de lignes peut inclure des valeurs agrégées et triées, des échantillons d'ensembles de lignes ou des ensembles de lignes croisés dynamiques et non croisés dynamiques.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation d'agrégation](aggregate-transformation.md)|Transformation qui effectue des agrégations telles que AVERAGE, SUM et COUNT.|  
|[Transformation de tri](sort-transformation.md)|Transformation qui trie des données.|  
|[Transformation de l'échantillonnage du pourcentage](percentage-sampling-transformation.md)|Transformation qui crée un échantillon de jeu de données avec un pourcentage spécifiant la taille d'échantillonnage.|  
|[Transformation d'échantillonnage de lignes](row-sampling-transformation.md)|Transformation qui crée un échantillon de jeu de données en spécifiant le nombre de lignes de l'échantillon.|  
|[Transformation de tableau croisé dynamique](pivot-transformation.md)|Transformation qui crée une version moins normalisée d'une table normalisée.|  
|[Transformation Unpivot](unpivot-transformation.md)|Transformation qui crée une version plus normalisée d'une table non normalisée.|  
  
## <a name="split-and-join-transformations"></a>Transformations de fractionnement et de jointure  
 Les transformations suivantes distribuent des lignes vers différentes sorties, créent des copies des entrées de transformation, joignent plusieurs entrées en une même entrée et effectuent des opérations de recherche.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation de fractionnement conditionnel](conditional-split-transformation.md)|Transformation qui achemine des lignes de données vers différentes sorties.|  
|[Transformation de multidiffusion](multicast-transformation.md)|Transformation qui distribue des jeux de données vers différentes sorties.|  
|[Transformation d'union totale](union-all-transformation.md)|Transformation qui fusionne plusieurs jeux de données.|  
|[Transformation de fusion](merge-transformation.md)|Transformation qui fusionne deux jeux de données triés.|  
|[Transformation de jointure de fusion](merge-join-transformation.md)|Transformation qui joint deux jeux de données à l'aide d'une jointure FULL, LEFT ou INNER.|  
|[Transformation de recherche](lookup-transformation.md)|Transformation qui recherche des valeurs dans une table de référence au moyen d'une correspondance exacte.|  
|[Transformation du cache](cache-transform.md)|Transformation qui écrit les données d'une source de données connectée du flux de données dans un gestionnaire de connexions du cache qui enregistre les données dans un fichier cache. La transformation de recherche effectue des recherches sur les données dans le fichier cache.|  
|[Transformation du distributeur de données équilibrées (BDD)](balanced-data-distributor-transformation.md)|La transformation distribue des tampons de lignes entrantes uniformément dans les sorties sur des threads distincts pour améliorer les performances des packages SSIS en cours d'exécution sur des serveurs à plusieurs cœurs et plusieurs processeurs.|  
  
## <a name="auditing-transformations"></a>Audit des transformations  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] inclut les transformations suivantes pour ajouter des informations d’audit et compter le nombre de lignes.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Transformation d'audit](audit-transformation.md)|Transformation qui rend les informations sur l'environnement accessibles au flux de données d'un package.|  
|[Transformation de calcul du nombre de lignes](row-count-transformation.md)|Transformation qui compte des lignes à mesure qu'elle les parcourt et stocke le nombre final dans une variable.|  
  
## <a name="custom-transformations"></a>Transformations personnalisées  
 Vous pouvez également écrire des transformations personnalisées. Pour plus d’informations, consultez [Développement d’un composant de transformation personnalisé à sorties synchrones](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) et [Développement d’un composant de transformation personnalisé à sorties asynchrones](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).  
  
  
