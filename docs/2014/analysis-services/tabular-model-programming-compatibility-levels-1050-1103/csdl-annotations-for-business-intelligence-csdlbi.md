---
title: Annotations CSDL pour Business Intelligence (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: bf6f372a-bc67-45ea-a771-b2dc5b0527e5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 760e90c34c84bd4b44af90cbbb78aec7e025689a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757953"
---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a>Annotations CSDL pour Business Intelligence (CSDLBI)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge la présentation de la définition d'un modèle tabulaire dans un format XML appelé langage CSDL (Conceptual Schema Definition Langage) avec des annotations Business Intelligence (CSDLBI).  
  
 Cette rubrique fournit une vue d'ensemble de CSDLBI et de son utilisation avec des modèles de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="understanding-the-role-of-csdl"></a>Comprendre le rôle du langage CSDL  
 CSDL est un langage basé sur XML qui décrit des entités, des relations et des fonctions. Le langage CSDL est défini dans le cadre de l'Entity Data Framework. Les annotations BI sont une extension conçue pour prendre en charge la modélisation des données à l'aide d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Bien que le langage CSDL soit compatible avec l'Entity Data Framework, vous n'avez pas besoin de comprendre le modèle de relation d'entité et vous n'avez pas non plus besoin d'outils spéciaux pour générer un modèle tabulaire ou un rapport basé sur un modèle. Pour générer des modèles, utilisez des outils clients tels que [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou une API telle que AMO, puis déployez le modèle sur un serveur. Pour se connectent au modèle les clients utilisent un fichier de définition de modèle, généralement publié dans une bibliothèque SharePoint où il pourra être utilisé par les concepteurs de rapports et les consommateurs de rapports. Pour plus d'informations, consultez ces liens :  
  
-   [Solutions de modèles tabulaires &#40;SSAS Tabulaire&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
-   [Déploiement d’une solution de modèle tabulaire &#40;SSAS Tabulaire&#41;](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
-   [Connexion de modèle sémantique BI PowerPivot &#40;.bism&#41;](../power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)  
  
 Le schéma CSDLBI est généré par le serveur Analysis Services en réponse à une demande d'une définition de modèle d'un client de création de rapports, tel que [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. L'application cliente envoie une requête XML au serveur Analysis Services qui héberge les données du modèle. En réponse, le serveur envoie un message XML contenant une définition des entités du modèle, en utilisant les annotations CSDLBI. Le client du rapport utilise ensuite des informations pour présenter les champs, les agrégations et les mesures qui sont disponibles dans le modèle. Les annotations CSDLBI fournissent également des informations sur le regroupement, le tri et la mise en forme des données.  
  
 Pour obtenir des informations générales sur CSDLBI, consultez [Concepts CSDLBI](https://docs.microsoft.com/bi-reference/csdl/csdlbi-concepts).  
  
### <a name="working-with-csdl"></a>Utilisation de CSDL  
 L'ensemble d'annotations CSDLBI qui représente n'importe quel modèle tabulaire est un document XML qui contient une collection d'entités, simples et complexes. Les entités définissent des tables (ou dimensions), des colonnes (attributs), des associations (relations) et des formules incluses dans des colonnes calculées, des mesures ou des indicateurs de performance clés.  
  
 Vous ne pouvez pas modifier directement ces objets, mais vous devez utiliser les outils clients et des API (interfaces de programmation d'applications) fournis pour utiliser des modèles tabulaires.  
  
 Vous pouvez obtenir le langage CSDL pour un modèle en envoyant une demande DISCOVER au serveur qui héberge le modèle. La demande doit être qualifiée en spécifiant le serveur et le modèle, et, éventuellement, une vue ou une perspective. Le message retourné est une chaîne XML. Certains éléments dépendent du langage et peuvent retourner des valeurs différentes selon le langage de la connexion actuelle. Pour plus d’informations, consultez [ensemble de lignes DISCOVER_CSDL_METADATA](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).  
  
### <a name="csdlbi-versions"></a>Versions de CSDLBI  
 La spécification CSDL d'origine (Entity Data Framework) prévoit la plupart des entités et des propriétés exigées pour prendre en charge la modélisation. Les annotations BI prennent en charge les spécifications particulières des modèles tabulaires, les propriétés de création de rapports requises pour les clients, tels que [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], et les métadonnées supplémentaires requises pour les modèles multidimensionnels. Cette section décrit les mises à jour dans chaque version.  
  
 **CSDLBI 1.0**  
  
 Le jeu initial d'ajouts au schéma CSDL pour prendre en charge les modèles tabulaires [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenait des annotations afin de prendre en charge la modélisation des données, les calculs personnalisés et la présentation avancée :  
  
-   Nouveaux éléments et propriétés pour prendre en charge les modèles tabulaires. Par exemple, une propriété a été ajoutée pour spécifier le type de requête de base de données utilisé pour remplir le modèle.  
  
-   Nouvelles propriétés et extensions dans les entités existantes.  Par exemple, l'élément Association a été étendu pour prendre en charge les relations.  
  
-   Propriétés de visualisation et de navigation. Par exemple, des propriétés ont été ajoutées pour prendre en charge les champs de tri personnalisé, les images par défaut et  
  
 **CSDLBI 1.1**  
  
 Cette version du schéma CSDLBI inclut des ajouts pour la prise en charge des bases de données multidimensionnelles (telles que les cubes OLAP). Les nouveaux éléments et propriétés sont les suivants :  
  
-   Prise en charge des dimensions sous la forme d'entités.  
  
-   Prise en charge des hiérarchies.  
  
-   Expose les partitions ROLAP.  
  
-   Prise en charge des traductions.  
  
-   Prise en charge des perspectives.  
  
 Pour plus d’informations sur les éléments individuels dans les annotations CSDLBI, consultez [informations techniques de référence pour les Annotations BI au langage CSDL](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl). Pour plus d’informations sur la spécification CSDL principale, consultez le [spécification CSDL v3](https://docs.microsoft.com/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).  
  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation du modèle d’objet tabulaire](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Concepts CSDLBI](https://docs.microsoft.com/bi-reference/csdl/csdlbi-concepts)   
 [Présentation du modèle d’objet tabulaire](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
