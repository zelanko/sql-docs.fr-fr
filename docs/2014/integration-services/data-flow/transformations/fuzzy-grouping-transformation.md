---
title: Regroupement approximatif, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtrans.f1
helpviewer_keywords:
- cleaning data
- comparing data
- token delimiters [Integration Services]
- temporary indexes [Integration Services]
- Fuzzy Grouping transformation
- temporary tables [Integration Services]
- grouping data
- standardizing data [Integration Services]
- columns [Integration Services], standardizing
- similarity thresholds [Integration Services]
- data cleaning [Integration Services]
- duplicate data [Integration Services]
ms.assetid: e43f17bd-9d13-4a8f-9f29-cce44cac1025
caps.latest.revision: 58
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4d5c49bcf93c7b80ab60341136dbcae4e16c94a5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209379"
---
# <a name="fuzzy-grouping-transformation"></a>Transformation de regroupement approximatif
  La transformation de regroupement probable effectue des tâches de nettoyage des données en identifiant les lignes de données susceptibles d'être des doublons et en sélectionnant une ligne canonique de données à utiliser pour standardiser les données.  
  
> [!NOTE]  
>  Pour plus d’informations sur la transformation de regroupement floue, y compris les limitations en termes de performances et de mémoire, consultez le livre blanc, [Présentation des transformations Fuzzy Lookup (recherche approximative) et Fuzzy Grouping (regroupement approximatif) dans les services DTS (Data Transformation Services) de SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=96604).  
  
 La transformation de regroupement approximatif nécessite une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour créer les tables temporaires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nécessaires à l'algorithme de transformation. La connexion doit correspondre à un utilisateur disposant de l'autorisation de créer des tables dans la base de données.  
  
 Pour configurer la transformation, vous devez sélectionner les colonnes d'entrée à utiliser lors de l'identification des doublons, et vous devez sélectionner le type de correspondance (approximative ou exacte) pour chaque colonne. Une correspondance exacte garantit que seules les lignes possédant des valeurs identiques dans cette colonne seront regroupées. La correspondance exacte peut être appliquée aux colonnes de n'importe quel type de données [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , à l'exception des types DT_TEXT, DT_NTEXT et DT_IMAGE. Une correspondance approximative regroupe des lignes ayant à peu près les mêmes valeurs. La méthode utilisée pour la correspondance approximative des données est basée sur un score de similarité spécifié par l'utilisateur. Seules les colonnes avec les types de données DT_WSTR et DT_STR peuvent être utilisées dans la correspondance approximative. Pour plus d’informations, consultez [Types de données Integration Services](../integration-services-data-types.md).  
  
 La sortie de transformation comprend toutes les colonnes d'entrée, une ou plusieurs colonnes avec des données standardisées et une colonne contenant le score de similarité. Le score est représenté par une valeur décimale entre 0 et 1. La ligne canonique obtient le score de 1. Les scores des autres lignes dans le regroupement probable indiquent leur degré de correspondance avec cette ligne canonique. Plus le score se rapproche de 1, plus la ligne correspond à la ligne canonique. Si le regroupement probable comprend des lignes qui sont des doublons exacts de la ligne canonique, ces lignes ont également pour score la valeur 1. La transformation ne supprime pas les lignes dupliquées, mais les regroupe en créant une clé qui associe la ligne canonique à des lignes similaires.  
  
 La transformation produit une ligne de sortie pour chaque ligne d'entrée, avec les colonnes supplémentaires suivantes :  
  
-   **_key_in**, une colonne qui identifie chaque ligne de manière unique.  
  
-   **_key_out**, une colonne qui identifie un groupe de lignes dupliquées. La colonne **_key_out** a la même valeur que la colonne **_key_in** dans la ligne de données canonique. Les lignes ayant une valeur identique dans **_key_out** font partie du même groupe. La valeur **_key_out**pour un groupe correspond à la valeur **_key_in** dans la ligne de données canonique.  
  
-   **_score**, valeur comprise entre 0 et 1, qui indique la similarité de la ligne d’entrée avec la ligne canonique.  
  
 Il s'agit des noms de colonne par défaut ; vous pouvez configurer la transformation de regroupement probable pour utiliser d'autres noms. La sortie fournit également un score de similarité pour chaque colonne participant à un regroupement probable.  
  
 La transformation de regroupement probable comprend deux fonctionnalités de personnalisation du regroupement qu'elle effectue : les séparateurs de jetons et les seuils de similarité. La transformation fournit un ensemble par défaut de délimiteurs utilisés pour marquer des données, mais vous pouvez ajouter de nouveaux délimiteurs pour améliorer la création de jetons pour vos données.  
  
 Le seuil de similarité indique le degré de précision avec lequel la transformation identifie les doublons. Les seuils de similarité peuvent être définis au niveau du composant et de la colonne. Le seuil de similarité n'est disponible que pour les colonnes participant à une correspondance approximative. La plage de similarité va de 0 à 1. Plus le seuil s'approche de 1, plus les lignes et les colonnes doivent être similaires pour être répertoriées comme doublons. Vous spécifiez le seuil de similarité en définissant la propriété MinSimilarity au niveau du composant et de la colonne. Pour obtenir la similarité spécifiée au niveau du composant, toutes les lignes doivent montrer une similarité à travers toutes les colonnes qui est supérieure ou égale au seuil de similarité spécifié au niveau du composant.  
  
 La transformation de regroupement probable calcule les mesures internes de similarité ; les lignes moins similaires à la valeur spécifiée dans MinSimilarity ne sont pas regroupées.  
  
 Pour identifier un seuil de similarité qui fonctionne pour vos données, vous pouvez avoir à appliquer la transformation de regroupement probable plusieurs fois, avec des seuils de similarité minimale différents. Lors de l'exécution, les colonnes de score dans la sortie de la transformation contiennent les scores de similarité pour chaque ligne d'un groupe. Vous pouvez utiliser ces valeurs pour identifier le seuil de similarité approprié pour vos données. Si vous voulez augmenter la similarité, vous devez donner à MinSimilarity une valeur supérieure à celle des colonnes de score.  
  
 Vous pouvez personnaliser le regroupement effectué par la transformation en définissant les propriétés des colonnes dans l'entrée de la transformation du regroupement probable. Par exemple, la propriété FuzzyComparisonFlags spécifie comment la transformation compare les données de chaîne dans une colonne, et la propriété ExactFuzzy indique si la transformation effectue une correspondance approximative ou exacte.  
  
 Vous pouvez configurer la quantité de mémoire utilisée par la transformation de regroupement probable en définissant la propriété personnalisée MaxMemoryUsage. Vous pouvez spécifier le nombre de mégaoctets (Mo) ou utiliser la valeur 0 pour permettre à la transformation d'utiliser une quantité dynamique de mémoire en fonction de ses besoins et de la mémoire physique disponible. La propriété personnalisée MaxMemoryUsage peut être mise à jour par une expression de la propriété au moment du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](transformation-custom-properties.md).  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="row-comparison"></a>Comparaison de lignes  
 Lorsque vous configurez la transformation de regroupement probable, vous pouvez spécifier l'algorithme de comparaison utilisé par la transformation pour comparer les lignes dans l'entrée de transformation. Si vous définissez la propriété Exhaustive sur `true`, la transformation compare chaque ligne dans l’entrée à chaque autre ligne dans l’entrée. Cet algorithme de comparaison peut produire des résultats plus précis, mais il peut ralentir la transformation, sauf si le nombre de lignes dans l'entrée est peu élevé. Pour éviter les problèmes de performances, il est recommandé de définir la propriété Exhaustive `true` uniquement lors du développement du package.  
  
## <a name="temporary-tables-and-indexes"></a>Tables et index temporaires  
 Au moment de l'exécution, la transformation de regroupement approximatif crée des objets temporaires, tels que des tables et des index, parfois de taille importante, dans la base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à laquelle la transformation se connecte. La taille des tables et des index est proportionnelle au nombre de lignes dans l'entrée de la transformation et au nombre de jetons créés par la transformation de regroupement probable.  
  
 La transformation exécute également des requêtes sur les tables temporaires. Vous devez donc envisager de connecter la transformation de regroupement probable à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]qui n’est pas en production, notamment si le serveur de production dispose d’un espace disque disponible limité.  
  
 Les performances de cette transformation peuvent s'améliorer si les tables et les index qu'elle utilise sont situés sur l'ordinateur local.  
  
## <a name="configuration-of-the-fuzzy-grouping-transformation"></a>Configuration de la transformation de regroupement probable  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de regroupement probable** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de Transformation de regroupement probable &#40;onglet Gestionnaire de connexions&#41;](../../fuzzy-grouping-transformation-editor-connection-manager-tab.md)  
  
-   [Éditeur de Transformation de regroupement probable &#40;onglet colonnes&#41;](../../fuzzy-grouping-transformation-editor-columns-tab.md)  
  
-   [Éditeur de Transformation de regroupement probable &#40;onglet Avancé&#41;](../../fuzzy-grouping-transformation-editor-advanced-tab.md)  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d'informations sur la définition des propriétés de cette tâche, cliquez sur l'une des rubriques suivantes :  
  
-   [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](fuzzy-grouping-transformation.md)  
  
-   [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de recherche floue](lookup-transformation.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
