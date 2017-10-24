---
title: "Configurer le stockage des chaînes pour les Partitions et Dimensions | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 987f6cfc-da82-4b2e-96ef-a8af88339e5f
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cd8d940628f843407c7c841b73b1322096fda615
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="configure-string-storage-for-dimensions-and-partitions"></a>Configurer le stockage de chaînes pour des dimensions et des partitions
  Vous pouvez reconfigurer le stockage des chaînes pour adapter les chaînes de très grande taille dans les attributs de dimension ou les partitions qui dépassent la limite de taille de fichier de 4 Go pour les magasins de chaînes. Si vos dimensions ou partitions incluent des magasins de chaînes de cette taille, vous pouvez contourner cette contrainte de taille de fichier en modifiant la propriété **StringStoresCompatibilityLevel** au niveau de la dimension ou de la partition, pour les objets locaux et les objets liés (locaux ou distants).  
  
 Notez que vous pouvez augmenter le stockage des chaînes seulement sur les objets qui nécessitent une capacité supplémentaire. Dans la plupart des modèles multidimensionnels, des données de chaîne sont associées aux dimensions. Toutefois, les partitions qui contiennent des mesures de comptage distinctes sur les chaînes peuvent également bénéficier de ce paramètre. Le paramètre ne concernant que les chaînes, les données numériques ne sont pas affectées.  
  
 Les valeurs valides pour cette propriété sont les suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**1050**|Spécifie l'architecture de stockage de chaînes par défaut, assujettie à une limite de taille de fichier de 4 Go par magasin.|  
|**1100**|Spécifie le stockage de chaînes plus important, prend en charge jusqu'à 4 milliards de chaînes uniques par magasin.|  
  
> [!IMPORTANT]  
>  La modification des paramètres de stockage de chaînes d'un objet requiert que vous recyclez l'objet lui-même et tout objet dépendant. Le traitement est obligatoire pour compléter la procédure.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [À propos des magasins de chaînes](#bkmk_background)  
  
-   [Conditions préalables](#bkmk_prereq)  
  
-   [Étape 1 : définir la propriété StringStoreCompatiblityLevel dans les outils de données SQL Server](#bkmk_step1)  
  
-   [Étape 2 : traitement des objets](#bkmk_step2)  
  
##  <a name="bkmk_background"></a> À propos des magasins de chaînes  
 La configuration du stockage des chaînes est facultative, ce qui signifie que même les nouvelles bases de données que vous créez utilisent l'architecture du magasin de chaînes par défaut, dont la taille de fichier maximale est limitée à 4 Go. L'utilisation de l'architecture de stockage de chaînes plus important a un impact limité mais notable sur les performances. Vous devez l'utiliser uniquement si vos fichiers de stockage de chaînes s'approchent de ou atteignent la limite de 4 Go.  
  
> [!NOTE]  
>  Ce paramètre ne s'applique pas aux modèles d'exploration de données. Actuellement, il est toujours possible de rencontrer la limitation de taille de fichier en Go sur les modèles contenant des structures d'exploration de données.  
  
 Dans une base de données multidimensionnelle Analysis Services, les chaînes sont stockées séparément des données numériques pour permettre des optimisations selon les caractéristiques des données. Les données de chaîne se trouvent en général dans les attributs de dimension qui représentent des noms ou des descriptions. Il est également possible de trouver des données de chaîne dans des mesures de comptage de valeurs. Les données de chaîne peuvent également être utilisées dans les clés.  
  
 Vous pouvez identifier un magasin de chaînes par son extension de fichier (par exemple les fichiers .asstore, .bstore, .ksstore ou les fichiers .string). Par défaut, chacun de ces fichiers est limité à une taille maximale de 4 Go. Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous pouvez remplacer la taille de fichier maximale en spécifiant un autre mécanisme de stockage qui permette à un magasin de chaînes de croître selon les besoins.  
  
 Par opposition avec l'architecture de stockage de chaînes par défaut qui limite la taille du fichier physique, le stockage de chaînes plus important est basé sur un nombre maximal de chaînes. La limite maximale pour le stockage de chaînes plus important est de 4 milliards de chaînes uniques ou de 4 milliards d'enregistrements, l'élément qui atteint le premier cette limite étant applicable. Le stockage de chaînes plus important crée des enregistrements de taille égale, où chaque enregistrement est égal à une page de 64 Ko. Si vous avez des chaînes très longues qui ne rentre pas dans un seul enregistrement, votre limite effective sera inférieure à 4 milliards de chaînes.  
  
##  <a name="bkmk_prereq"></a> Conditions préalables  
 Vous devez avoir une version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou ultérieure d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Les dimensions et les partitions doivent utiliser le mode de stockage MOLAP.  
  
 Le niveau de compatibilité de la base de données doit être 1100. Si vous avez créé ou déployé une base de données en utilisant [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] et la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou ultérieure d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le niveau de compatibilité de la base de données est déjà défini à 1100. Si vous avez déplacé une base de données créée dans une version antérieure d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vers ssSQL11 ou ultérieur, vous devez mettre à jour le niveau de compatibilité. Pour les bases de données que vous déplacez, mais ne redéployez pas, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour définir le niveau de compatibilité. Pour plus d’informations, consultez [Niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
##  <a name="bkmk_step1"></a> Étape 1 : définir la propriété StringStoreCompatiblityLevel dans les outils de données SQL Server  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet qui contient les dimensions ou partitions à modifier.  
  
2.  Pour modifier le stockage de chaînes pour les dimensions, ouvrez l'Explorateur de solutions. Double-cliquez sur la dimension pour laquelle vous modifiez le stockage de chaînes.  
  
3.  Dans le Concepteur de dimensions, dans le volet Attributs, assurez-vous que le nœud parent de la dimension est sélectionné (par exemple, si la dimension est Clients, sélectionnez Clients et non l'un des attributs enfants).  
  
4.  Dans le volet Propriétés, dans la section Avancé, attribuez à **StringStoresCompatibilityLevel** la valeur **1100**. Recommencez pour les autres dimensions qui nécessitent un stockage plus important, sinon laissez les dimensions restantes définies sur la valeur **1050** .  
  
5.  Pour les partitions, ouvrez un cube à partir de l'Explorateur de solutions.  
  
6.  Cliquez sur l'onglet Partitions.  
  
7.  Développez la partition, sélectionnez la partition qui nécessite une capacité de stockage supplémentaire, puis modifiez la propriété **StringStoresCompatibilityLevel** .  
  
8.  Enregistrez le fichier.  
  
##  <a name="bkmk_step2"></a> Étape 2 : traitement des objets  
 La nouvelle architecture de stockage sera utilisée une fois que vous aurez traité les objets. Le traitement des objets prouve également que vous avez résolu les problèmes de limite de stockage parce que l'erreur qui signalait précédemment une condition de dépassement de capacité du magasin de chaînes ne devrait plus apparaître.  
  
-   Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la dimension que vous venez de modifier et sélectionnez **Traiter**.  
  
 Vous devez utiliser l'option Traiter entièrement sur chaque objet qui utilise la nouvelle architecture du magasin de chaînes. Avant le traitement, veillez à exécuter une analyse d'impact sur la dimension pour vérifier si les objets dépendants doivent aussi être retraités.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et approches de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/tools-and-approaches-for-processing-analysis-services.md)   
 [Options et paramètres de traitement &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)   
 [Traitement et Modes de stockage de partitions](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)   
 [Stockage de dimension](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)  
  
  

