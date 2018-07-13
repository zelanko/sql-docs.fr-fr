---
title: Scénarios de globalisation pour données multidimensionnelles Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple language support [Analysis Services]
- languages [Analysis Services]
- SSAS, international considerations
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- SQL Server Analysis Services, international considerations
- Analysis Services, international considerations
ms.assetid: e8af85ff-ef33-4659-a003-bb34578eb2a2
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0c8aeb19e6773b3f772ae0a62e7d72f647ee365e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185396"
---
# <a name="globalization-scenarios-for-analysis-services-multiidimensional"></a>Scénarios de globalisation pour données multidimensionnelles Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stocke et manipule des données multilingues et les métadonnées dans les deux modèles de données tabulaires et multidimensionnels. Le stockage des données est en Unicode (UTF-16), dans des jeux de caractères qui utilisent l'encodage Unicode. Si vous chargez des données ANSI dans un modèle de données, les caractères sont stockés à l'aide de points de code équivalents Unicode.  
  
 La prise en charge d'Unicode signifie qu' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peut stocker des données dans n'importe laquelle des langues prises en charge par les systèmes d'exploitation Windows clients et serveurs, ce qui autorise la lecture, l'écriture, le tri et la comparaison des données dans n'importe quel jeu de caractères utilisé sur un ordinateur Windows. Les applications clientes BI consommant des données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] peuvent représenter les données dans la langue choisie par l'utilisateur, en supposant que les données existent dans cette langue dans le modèle.  
  
 La prise en charge linguistique peut signifier différentes choses pour différentes personnes. La liste suivante répond à quelques questions courantes liées à la prise en charge des langues par Analysis Services.  
  
-   Les données, comme nous l'avons déjà dit, sont stockées dans n'importe quel jeu de caractères Unicode détecté sur un système d'exploitation client Windows.  
  
-   Les métadonnées, telles que les noms d'objets, les identificateurs et les descriptions, peuvent également être dans n'importe quel(le) langue et script Unicode. Cela est vrai même quand les outils et l'environnement sont dans une autre langue. Par exemple, dans un environnement de développement qui utilise la langue anglaise et un classement Latin dans toute la pile, vous pouvez inclure dans votre modèle un objet dont le nom contient des caractères cyrilliques.  
  
     Pour les modèles multidimensionnels uniquement, les légendes et les membres d'attributs peuvent être exprimés comme des traductions. Vous pouvez définir une ou plusieurs traductions, puis utiliser un identificateur de paramètres régionaux pour déterminer la traduction retournée au client. Pour plus d'informations, consultez [Fonctionnalités](#bkmk_features) plus loin dans cet article.  
  
-   Messages d’erreur, avertissement et d’information retournés à partir de la [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] moteur (msmdsrv) sont traduits dans les 43 langues prises en charge par Office et Office 365. Aucune configuration n'est nécessaire pour obtenir les messages dans une langue spécifique. Les paramètres régionaux de l'application cliente déterminent quelles chaînes sont retournées.  
  
-   Le fichier de configuration (msmdsrv.ini) et PowerShell AMO sont en anglais uniquement.  
  
-   Les fichiers journaux contiendront un mélange de messages localisés et en anglais, en supposant que vous avez installé un module linguistique sur le serveur Windows qui exécute Analysis Services.  
  
-   La documentation et les outils, tels que [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] et [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)], sont traduits dans les langues suivantes : allemand, chinois simplifié, chinois traditionnel, coréen, espagnol, français, italien, japonais, portugais (brésilien) et russe. Pour utiliser une version spécifique à la langue des outils, installez une version spécifique à la langue de SQL Server (par exemple, installez la version allemande de SQL Server pour obtenir Management Studio en allemand) ou exécutez le programme d’installation autonome dans la langue cible pour [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)].  
  
 Analysis Services vous permet de définir la langue, le classement et les traductions indépendamment dans toute la hiérarchie d'objets.  
  
 Voici quelques-uns des scénarios possibles grâce aux langues, aux classements et aux traductions :  
  
-   Un modèle de données fournit plusieurs légendes traduites pour que les noms et les valeurs des champs apparaissent dans la langue choisie par l'utilisateur. Pour les entreprises qui opèrent dans des pays bilingues comme le Canada, la Belgique ou la Suisse, la prise en charge de plusieurs langues dans les applications clientes et de serveur est une exigence de codage ordinaire. Ce scénario est possible grâce aux traductions et aux conversions monétaires. Voir [Fonctionnalités](#bkmk_features) ci-dessous pour plus d'informations et pour obtenir des liens.  
  
-   Les environnements de développement et de production sont géolocalisés dans différents pays. Il est de plus en plus courant de développer une solution dans un pays, puis de la déployer dans un autre. Savoir comment définir les propriétés de langue et de classement est essentiel si vous êtes chargé de la préparation d'une solution développée dans une langue et devant être déployée sur un serveur qui utilise un module linguistique différent. Définir ces propriétés vous permet de remplacer les valeurs par défaut héritées du système hôte d'origine. Pour plus d’informations, consultez la section [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) .  
  
##  <a name="bkmk_features"></a> Fonctionnalités de création d’une solution multidimensionnelle globalisée  
 [!INCLUDE[applies](../includes/applies-md.md)] Modèles de données multidimensionnels uniquement  
  
 Au niveau du client, les applications globalisées qui consomment ou manipulent [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] données multidimensionnelles peuvent utiliser les fonctionnalités multilingues et multiculturelles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:  
  
-   [Traductions &#40;Analysis Services&#41; ](translations-analysis-services.md) servent à incorporer plusieurs légendes pour un seul objet, où chaque chaîne traduite peut coexister avec autres traductions. Vous pouvez utiliser [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir les traductions pour la légende, la description et les types de comptes pour des cubes, des mesures, des dimensions et des attributs. Vous pouvez récupérer des données et des métadonnées à partir d'objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur lesquels des traductions ont été définies automatiquement en fournissant un identificateur local lors de la connexion à une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
     Pour apprendre à utiliser cette fonctionnalité, consultez la [leçon 9 : définition de perspectives et de traductions](lesson-9-defining-perspectives-and-translations.md) du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   [Conversions monétaires &#40;Analysis Services&#41; ](currency-conversions-analysis-services.md) s’effectue via des scripts MDX spécialisés qui convertissent des mesures contenant des données monétaires. Vous pouvez utiliser l'Assistant Business Intelligence de [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] pour générer un script MDX qui utilise une combinaison de données et de métadonnées issues de dimensions, d'attributs et de groupes de mesures pour convertir des mesures contenant des données monétaires.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Langues et classements &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)|Spécifiez la langue par défaut et le classement Windows pour une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Vos choix affectent les données et les métadonnées gérées par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|  
|[Traductions &#40;Analysis Services&#41;](translations-analysis-services.md)|Définir des traductions pour une [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données et les objets contenus dans la base de données. Cette rubrique explique comment [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] résout les demandes de données et de métadonnées traduites envoyées par les applications clientes.|  
|[Conversions monétaires &#40;Analysis Services&#41;](currency-conversions-analysis-services.md)|Définissez une conversion monétaire à l'aide de l'Assistant Business Intelligence.|  
|[Globalisation conseils et meilleures pratiques &#40;Analysis Services&#41;](globalization-tips-and-best-practices-analysis-services.md)|Passe en revue plusieurs pratiques de conception et de codage qui peuvent vous aider à éviter les problèmes liés aux données multilingues.|  
  
## <a name="see-also"></a>Voir aussi  
 [Internationalisation pour les Applications Windows](http://msdn.microsoft.com/library/windows/desktop/dd318661%28v=vs.85%29.aspx)   
 [Accédez au centre de développement](http://msdn.microsoft.com/goglobal/bb871628.aspx)   
 [Applications d’écriture Windows Store avec conception adaptative en fonction des paramètres régionaux](http://blogs.windows.com/buildingapps/2014/03/06/writing-windows-store-apps-with-locale-based-adaptive-design/)   
 [Développement d’applications Windows universelles avec c# et XAML](http://www.microsoftvirtualacademy.com/training-courses/developing-universal-windows-apps-with-c-and-xaml)  
  
  
