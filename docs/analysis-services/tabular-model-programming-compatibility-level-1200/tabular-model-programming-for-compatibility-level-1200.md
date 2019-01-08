---
title: Analysis Services (tabulaire) modèle de programmation pour le niveau de compatibilité 1200 | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eba8822f7fe21e089d9c02b8f6df6cf5ec0e5294
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072106"
---
# <a name="tabular-model-programming-for-compatibility-level-1200-and-higher"></a>Programmation de modèles tabulaires pour les niveaux de compatibilité 1200 et supérieurs
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
À compter de niveau de compatibilité 1200, les métadonnées tabulaires sont utilisée pour décrire les constructions de modèle, en remplaçant historiques métadonnées multidimensionnelles comme descripteurs pour les objets de modèle tabulaire. Métadonnées des tables, colonnes et relations sont table, colonne et de relation, plutôt que les équivalents multidimensionnelles (dimension et attribut).  
  
Vous pouvez créer de nouveaux modèles au niveau de compatibilité 1200 ou supérieur à l’aide de la APIs Microsoft.AnalysisServices.Tabular, la dernière version de SQL Server Data Tools (SSDT), ou en modifiant le **CompatibilityLevel** d’un tabulaire existante modèle à mettre à niveau (également effectuées dans SSDT). Cela lie le modèle à des versions plus récentes du serveur, des outils et des interfaces de programmation.   
  
La mise à niveau une solution tabulaire existante est recommandé, mais pas obligatoire. Script existant et des solutions personnalisées qui accèdent ou gérer les modèles tabulaires ou des bases de données peuvent être utilisées en tant que-est. Niveaux de compatibilité antérieurs sont entièrement pris en charge dans SQL Server 2016 avec les fonctionnalités disponibles à ce niveau. Azure Analysis Services prend en charge le niveau de compatibilité 1200 et versions ultérieures uniquement.
  
 Nouveaux modèles tabulaires nécessitera un code différent et script, résumées ci-dessous.  
  
## <a name="object-model-definitions-as-tabular-metadata-constructs"></a>Définitions de modèle d’objet comme des constructions de métadonnées tabulaires  
 Le modèle d’objet tabulaire pour les modèles 1200 ou supérieur est exposé au format JSON via le [Tabular Model Scripting Language](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) et via le langage de définition de données AMO via un nouvel espace de noms [ Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx)

## <a name="script-for-tabular-models-and-databases"></a>Script pour bases de données et les modèles tabulaires  
 TMSL est un langage de script JSON pour les modèles tabulaires, avec prise en charge pour la création, lecture, mise à jour, un opérations de suppression. Vous pouvez actualiser les données via TMSL et appeler des opérations de base de données pour attacher, detatch, sauvegarde, restauration et synchronisation.  
  
 AMO PowerShell accepte un script TMSL en tant qu’entrée.  
  
 Consultez [Tabular Model Scripting Language &#40;TMSL&#41; référence](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference) et [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md) pour plus d’informations.  
  
## <a name="query-languages"></a>Langages de requête  
 DAX et MDX sont prises en charge pour tous les modèles tabulaires.  
  
## <a name="expression-language"></a>Langage d’expression  
 Filtres et les expressions utilisées pour créer des objets calculés, y compris les mesures et indicateurs de performance clés sont formulées dans DAX. Consultez [comprendre DAX dans les modèles tabulaires](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md) et [Data Analysis Expressions &#40;DAX&#41; dans Analysis Services](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5).  
  
## <a name="managed-code-for-tabular-models-and-databases"></a>Code managé pour les modèles tabulaires et les bases de données  
 AMO comprend un nouvel espace de noms Microsoft.AnalysisServices.Tabular, pour l’utilisation des modèles par programme. Consultez [Microsoft.AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx) pour plus d’informations.  
  
> [!NOTE]  
>  Bibliothèques clientes Analysis Services Management Objects (AMO), ADOMD.NET et le modèle d’objet tabulaire (TOM) maintenant ciblent le runtime .NET 4.0.   
  
## <a name="see-also"></a>Voir aussi  
 [Documentation du développeur Analysis Services](../../analysis-services/analysis-services-developer-documentation.md)   
 [Programmation de modèle tabulaire pour assurer la compatibilité des niveaux 1050 à 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)   
 [Informations techniques de référence ](../../analysis-services/powershell/technical-reference-ssas.md) [mise à niveau d’Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
 [Niveaux de compatibilité des bases de données et les modèles tabulaires](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)  
  
  
