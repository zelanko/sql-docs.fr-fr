---
title: Scénarios de globalisation pour Analysis Services | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9af9e0eaf06fca60da515a16e7e6830dcb8462d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659694"
---
# <a name="globalization-scenarios-for-analysis-services"></a>Scénarios de globalisation pour Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stocke et traite des données et métadonnées multilingues dans les modèles de données tabulaires et multidimensionnels. Le stockage des données est en Unicode (UTF-16), dans des jeux de caractères qui utilisent l'encodage Unicode. Si vous chargez des données ANSI dans un modèle de données, les caractères sont stockés à l'aide de points de code équivalents Unicode.  
  
 La prise en charge d'Unicode signifie qu' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peut stocker des données dans n'importe laquelle des langues prises en charge par les systèmes d'exploitation Windows clients et serveurs, ce qui autorise la lecture, l'écriture, le tri et la comparaison des données dans n'importe quel jeu de caractères utilisé sur un ordinateur Windows. Les applications clientes BI consommant des données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peuvent représenter les données dans la langue choisie par l'utilisateur, en supposant que les données existent dans cette langue dans le modèle.  
  
 La prise en charge linguistique peut signifier différentes choses pour différentes personnes. La liste suivante répond à quelques questions courantes liées à la prise en charge des langues par Analysis Services.  
  
-   Les données, comme nous l'avons déjà dit, sont stockées dans n'importe quel jeu de caractères Unicode détecté sur un système d'exploitation client Windows.  
  
-   Les métadonnées, telles que les noms d’objet, peuvent être traduites. Bien que la prise en charge varie selon le type de modèle, les modèles multidimensionnels et tabulaires autorisent l’ajout de chaînes traduites. Vous pouvez définir plusieurs traductions, puis utiliser un identificateur de paramètres régionaux pour déterminer la traduction renvoyée au client. Pour plus d’informations, consultez la section [Fonctionnalités](#bkmk_features) plus avant.  
  
-   Les messages d’erreur, d’avertissement et d’information renvoyés par le moteur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (msmdsrv) sont traduits dans les 43 langues prises en charge par Office et Office 365. Aucune configuration n'est requise pour obtenir les messages dans une langue spécifique. Les paramètres régionaux de l'application cliente déterminent quelles chaînes sont retournées.  
  
-   Le fichier de configuration (msmdsrv.ini) et PowerShell AMO sont en anglais uniquement.  
  
-   Les fichiers journaux contiendront un mélange de messages localisés et en anglais, en supposant que vous avez installé un module linguistique sur le serveur Windows qui exécute Analysis Services.  
  
-   Documentation et les outils, tels que [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] et [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], sont traduits dans les langues suivantes : Chinois simplifié, chinois traditionnel, Français, allemand, italien, japonais, coréen, portugais (Brésil), russe et espagnol. La culture est spécifiée lors de l’installation.  
  
 Dans les modèles multidimensionnels, Analysis Services vous permet de définir la langue, le classement et les traductions indépendamment dans toute la hiérarchie d’objets.  Dans les modèles tabulaires, vous ne pouvez qu’ajouter des traductions : la langue et le classement sont gérés par le système d’exploitation hôte.  
  
 Les scénarios rendus possibles par les fonctionnalités de globalisation d’Analysis Services sont les suivants :  
  
-   Un modèle de données fournit plusieurs légendes traduites pour que les noms et les valeurs des champs apparaissent dans la langue choisie par l'utilisateur. Pour les entreprises qui opèrent dans des pays bilingues comme le Canada, la Belgique ou la Suisse, la prise en charge de plusieurs langues dans les applications clientes et de serveur est une exigence de codage ordinaire. Ce scénario est possible grâce aux traductions et aux conversions monétaires. Voir [Fonctionnalités](#bkmk_features) ci-dessous pour plus d'informations et pour obtenir des liens.  
  
-   Les environnements de développement et de production sont géolocalisés dans différents pays. Il est de plus en plus courant de développer une solution dans un pays, puis de la déployer dans un autre. Savoir comment définir les propriétés de langue et de classement est essentiel si vous êtes chargé de la préparation d'une solution développée dans une langue et devant être déployée sur un serveur qui utilise un module linguistique différent. Définir ces propriétés vous permet de remplacer les valeurs par défaut héritées du système hôte d'origine. Pour plus d’informations, consultez la section [Langues et classements &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md) .  
  
##  <a name="bkmk_features"></a> Fonctionnalités de création d’une solution multidimensionnelle globalisée  
 Au niveau du client, les applications globalisées qui consomment ou traitent des données multidimensionnelles [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peuvent utiliser les fonctionnalités multilingues et multiculturelles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Vous pouvez récupérer des données et des métadonnées à partir d'objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur lesquels des traductions ont été définies automatiquement en fournissant un identificateur local lors de la connexion à une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 Pour passer en revue les pratiques de conception et de codage qui peuvent vous aider à éviter les problèmes liés aux données multilingues, consultez [Conseils et meilleures pratiques en matière de globalisation &#40;Analysis Services&#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md).  
  
||||  
|-|-|-|  
|**Fonctionnalité**|**Tabulaire**|**(Multidimensionnel)**|  
|[Langues et classements &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md)|Héritée du système d’exploitation.|Héritée, mais avec la possibilité de remplacer la langue et le classement des objets principaux dans la hiérarchie du modèle.|  
|Étendue de la prise en charge de la traduction|Légendes et descriptions.|Vous pouvez traduire les noms d’objet, les légendes, les identificateurs et les descriptions dans n’importe quel script et langage Unicode. Cela est vrai même quand les outils et l'environnement sont dans une autre langue. Par exemple, dans un environnement de développement qui utilise la langue anglaise et un classement Latin dans toute la pile, vous pouvez inclure dans votre modèle un objet dont le nom contient des caractères cyrilliques.|  
|Implémentation de la prise en charge de la traduction|Utilisez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour générer des fichiers de traduction que vous complétez et réimporter dans le modèle.<br /><br /> Pour plus d’informations, consultez [Traductions dans les modèles tabulaires &#40;Analysis Services&#41;](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md).|Utilisez[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir les traductions de la légende, de la description et des types de compte des cubes, mesures, dimensions et attributs.<br /><br /> Pour plus d’informations, consultez [Traductions dans les modèles multidimensionnels &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md). Vous trouverez une leçon sur la façon d’utiliser cette fonctionnalité dans [leçon 9 : Définition de Perspectives et traductions](../analysis-services/lesson-9-defining-perspectives-and-translations.md) de la [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] didacticiel.|  
|Conversion monétaire|Non disponible.|La conversion monétaire s’effectue à l’aide de scripts MDX spécialisés qui convertissent les mesures contenant des données monétaires. Vous pouvez utiliser l'Assistant Business Intelligence de [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] pour générer un script MDX qui utilise une combinaison de données et de métadonnées issues de dimensions, d'attributs et de groupes de mesures pour convertir des mesures contenant des données monétaires. Consultez [Conversions monétaires &#40;Analysis Services&#41;](../analysis-services/currency-conversions-analysis-services.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des traductions dans Analysis Services](../analysis-services/translation-support-in-analysis-services.md)   
 [Internationalisation pour les applications Windows](http://msdn.microsoft.com/library/windows/desktop/dd318661%28v=vs.85%29.aspx)   
 [Globalisation](/globalization/)   
 [Écriture d’applications du Windows Store avec la conception adaptative en fonction des paramètres régionaux](https://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/)   
 [Développement d'applications Windows universelles avec C# et XAML](http://www.microsoftvirtualacademy.com/training-courses/developing-universal-windows-apps-with-c-and-xaml)  
  
  
