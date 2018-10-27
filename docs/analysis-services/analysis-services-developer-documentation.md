---
title: Documentation du développeur Analysis Services | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b0932c9ebcd2d516a5bfb0e6ea5608501e4f514a
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146095"
---
# <a name="analysis-services-developer-documentation"></a>Documentation du développeur Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

Dans Analysis Services, presque tous les objets et la charge de travail sont programmable, et souvent, il existe plusieurs approches sélectionnables.  Options incluent l’écriture de code managé, script ou à l’aide de normes ouvertes telles que XMLA et MSOLAP si les besoins de votre solution fait obstacle à l’aide de .NET framework.

## <a name="what-you-can-accomplish-in-code"></a>Ce que vous pouvez accomplir dans le code
Les scénarios de programmation classiques incluent le serveur et de déploiement de base de données, l’administration, modèle et la création de base de données et accès aux données à partir de vos applications personnalisées et les rapports qui utilisent des données Analysis Services. Commune à tous ces scénarios est une hiérarchie définition architecture et d’objet fixe, avec des opérations bien comprises qui s’étendent sur la définition de données, de traitement et de charges de travail de requête.

Bien que les objets et les charges de travail sont programmables, elles ne sont pas extensibles. Plus précisément, vous ne pouvez pas créer cartouches personnalisé permettant de récupérer des données à partir de sources de données non pris en charge, personnaliser ou remplacement les comportements de moteur de formule ou de stockage, ni de créer de nouveaux types de métadonnées d’objet sur un serveur, la base de données ou le modèle.

En dire plus sur le dernier point sur la création de nouveaux types d’objets : vous ne pouvez pas créer un nouveau type d’objet, vous pouvez créer des objets calculées créés à partir des expressions ou du code en cours d’exécution. Pas tous les éléments de votre modèle doivent être prédéfinies et mappée à une structure de données existante. En outre, vous pouvez étendre le schéma via des Annotations dans AMO pour passer des informations d’objet spécifique à votre application cliente.

## <a name="choose-a-platform-or-approach-to-development"></a>Choisissez une plateforme ou une approche du développement
Analysis Services fournit plusieurs façons de personnaliser une solution via le code, mais la plupart des développeurs utilisent l’API managée ou un script.

- Incluent des API managées [AMO et TOM](http://msdn.microsoft.com/library/mt436122.aspx) pour la définition de données et les tâches d’administration, et [ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) pour la prise en charge des requêtes depuis le code client. Dans SQL Server 2016, AMO est mis à jour pour utiliser les nouvelles métadonnées tabulaires pour les modèles créés ou mis à niveau vers le niveau de compatibilité 1200 et supérieur.

- Script peut souvent obtenir les mêmes résultats en tant que programme exécutable, avec éventuellement moins de travail.

  - Vous pouvez écrire le script PowerShell à l’aide de composants de PowerShell Analysis Services qui appellent directement des types AMO. Dans PowerShell, vous pouvez également créer et exécuter/XMLA ASSL ou TMSL (dans JSON).

  - ASSL et TMSL sont des langages de script qui fournissent des objets utilisés dans les découvrir et exécuter des opérations. Le type de script que vous utilisez dépend du serveur, base de données ou modèle sous-jacent.

  - Les modèles tabulaires ou des bases de données au niveau de compatibilité 1200 et versions ultérieures utilisent le modèle tabulaire Scripting Language (TMSL), qui est au format JSON.

  - Les modèles multidimensionnels et les modèles tabulaires aux niveaux de compatibilité 1050-1103 utilisent Analysis Services Scripting Language (ASSL), qui est l’extension de la norme ouverte XMLA Analysis Services.

  - Vous pouvez générer le script ASSL ou TMSL dans Management Studio. Vous pouvez également utiliser **afficher le Code** dans SQL Server Data Tools pour afficher la définition de modèle dans ASSL ou TMSL.

- Bien qu’il soit possible de créer une solution basée sur les normes ouvertes de XMLA et MDX, il est très rare de faire. Il n’existe aucune documentation autre que XMLA et dessine des référence MDX pour vous et la plupart des Communautés et forum prennent en charge à partir des expériences avec .NET ou les technologies natives (MSOLAP).

## <a name="programming-in-analysis-services"></a>Programmation dans Analysis Services
[Programmation de données d’exploration de données](../analysis-services/data-mining-programming.md) décrit les approches de création de solutions qui incluent des objets d’exploration de données.

[Programmation de modèle multidimensionnel](../analysis-services/multidimensional-models/multidimensional-model-programming.md) décrit les tâches de développement et les approches d’intégration des objets de modèle multidimensionnel dans une solution personnalisée.

[Tabulaire modèle de programmation pour le niveau de compatibilité 1200 et supérieur](../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)
**nouveau dans SQL Server 2016**.  Résume les interfaces et langages de script utilisées pour travailler avec les modèles plus élevés et de 1200 tabulaires par programmation.

[Programmation de modèles tabulaires pour les niveaux de compatibilité 1050 à 1103](../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md) cette documentation est destinée aux développeurs qui prennent en charge les modèles tabulaires aux niveaux de compatibilité antérieure. Il décrit les extensions CSDL qui définissent un modèle tabulaire dans la syntaxe XML. Il inclut également des informations sur la syntaxe et les définitions de modèle d’objet tabulaire.

[Analysis Services Management Objects (AMO)](https://msdn.microsoft.com/library/mt436122.aspx) documentation référence du développeur pour le fournisseur managé, Analysis Services Management Objects (AMO), pour la définition de données et d’administration, y compris le traitement.

[ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx) Developer documentation de référence sur le fournisseur managé, ADOMD.NET, utilisé pour les données par programmation les charges de travail accès et de la requête.

[Ensembles de lignes de schéma Analysis Services](https://docs.microsoft.com/bi-reference/schema-rowsets/analysis-services-schema-rowsets) décrit les ensembles de lignes de schéma qui fournissent des informations sur l’état du serveur, les opérations de serveur et les objets de base de données.

[XML for Analysis &#40;XMLA&#41; référence](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) concepts XMLA décrit qui peuvent vous aider à comprennent comment XMLA contribue à votre solution personnalisée. Décrit également le niveau de compatibilité avec la spécification XMLA 1.1.

[Analysis Services Scripting Language &#40;ASSL pour XMLA&#41; ](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) décrit les extensions ASSL à XMLA. ASSL propose un langage de manipulation et de définition de données pour les modèles multidimensionnels Analysis Services qui complète la spécification XMLA.

[Tabular Model Scripting Language &#40;TMSL&#41; référence](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) TMSL est une représentation JSON de modèles tabulaires au niveau de compatibilité 1200 et supérieur. Définitions d’objet sont basées sur des constructions de métadonnées tabulaires telles que la table, colonne et relation plutôt que des métadonnées multidimensionnelles qui peuvent être peu familières si vous débutez avec modélisation de données Analysis Services en mode tabulaire.

[Analysis Services PowerShell Reference](../analysis-services/powershell/analysis-services-powershell-reference.md) documente les applets de commande utilisé pour les fonctions d’administration, ainsi que l’usage général **Invoke-ASCmd** applet de commande qui accepte n’importe quel script ou une requête en tant qu’entrée.

## <a name="see-also"></a>Voir aussi
[Informations techniques de référence ](../analysis-services/powershell/technical-reference-ssas.md) 
 [de requêtes et de référence de langage d’Expression &#40;Analysis Services&#41;](http://msdn.microsoft.com/library/gg492188.aspx)
