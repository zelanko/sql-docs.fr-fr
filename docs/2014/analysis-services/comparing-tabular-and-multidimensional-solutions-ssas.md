---
title: Comparaison des solutions tabulaires et multidimensionnelles (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 76ee5e96-6a04-49af-a88e-cb5fe29f2e9a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1da4224387e70ccc76e069aa3ce411dddb79b805
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087770"
---
# <a name="comparing-tabular-and-multidimensional-solutions-ssas"></a>Comparaison des solutions tabulaires et multidimensionnelles (SSAS)
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]fournit deux approches distinctes pour la modélisation des données : tabulaire et multidimensionnel. Bien qu'elles présentent de nombreux points communs, elles ont aussi d'importantes différences qui guideront votre choix. Dans cette rubrique, nous comparons les fonctionnalités et décrivons la façon dont chaque approche répond aux besoins communs des projets. Par exemple, si la prise en charge d'une source de données spécifique est prioritaire, la section sur les sources de données peut vous aider à choisir l'approche de modélisation qui convient.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Vue d'ensemble de la modélisation dans Analysis Services](#bkmk_overview)  
  
-   [Prise en charge des sources de données par type de solution](#bkmk_ds)  
  
-   [Fonctionnalités du modèle](#bkmk_models)  
  
-   [Taille des modèles](#bkmk_modelsize)  
  
-   [Programmabilité et expérience des développeurs](#bkmk_ext)  
  
-   [Prise en charge des langages de requête et de script](#bkmk_lang)  
  
-   [Prise en charge des fonctionnalités de sécurité](#bkmk_sec)  
  
-   [Outils de conception](#bkmk_designer)  
  
-   [Applications clientes et de création de rapports](#bkmk_client)  
  
-   [Plateformes d'hébergement](#bkmk_sharePoint)  
  
-   [Modes de déploiement de serveur pour les solutions multidimensionnelles et tabulaires](#bkmk_deploymentmode)  
  
-   [Étape suivante : générer une solution](#bkmk_Next)  
  
 Vous trouverez des informations supplémentaires dans cet article technique sur MSDN : [Choisir une expérience de modélisation tabulaire ou multidimensionnelle dans SQL Server 2012 Analysis Services](https://go.microsoft.com/fwlink/?LinkId=251588).  
  
##  <a name="bkmk_overview"></a>Vue d’ensemble de la modélisation dans Analysis Services  
 Analysis Services permet de développer et déployer des modèles via l'hébergement de base de données sur une instance Analysis Services. Les types de modèle sont tabulaires ou multidimensionnels. Comme l'on peut s'y attendre, l'hébergement de base de données prend en charge les solutions multidimensionnelles et tabulaires que vous créez, mais l'hébergement de base de données inclut également PowerPivot pour SharePoint.  
  
 PowerPivot pour SharePoint représente *Analysis Services en mode SharePoint*, où Analysis Services fonctionne comme un service complémentaire de SharePoint, permettant d'héberger et de gérer les modèles de données Excel créés au préalable dans Excel, puis enregistrés dans SharePoint. Le rôle d'Analysis Services dans ce contexte consiste à charger le modèle de données en mémoire, d'actualiser les données à partir de sources de données externes et d'exécuter des requêtes sur le modèle. Dans cette configuration, Analysis Services s'exécute en arrière-plan. Toutes les demandes et les connexions à Analysis Services sont effectuées par SharePoint et uniquement quand un classeur Excel contient un modèle de données (les modèles de données sont facultatifs dans les classeurs Excel). Si vous créez un modèle de données dans Excel et que vous l’hébergez dans SharePoint, vous les Alignez avec les exigences de votre projet, consultez [Power Pivot : analyse de données et modélisation des données puissantes dans Excel](https://support.office.com/en-ie/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-d7b119ed-1b3b-4f23-b634-445ab141b59b) et [PowerPivot pour SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md) pour plus d’informations.  
  
> [!NOTE]  
>  Les modèles de données Excel et les modèles tabulaires ont une architecture similaire. Si vous devez prendre en charge de grandes quantités de données ou utiliser d'autres fonctionnalités de modèle non disponibles dans Excel, vous pouvez importer un modèle de données Excel dans un modèle tabulaire.  
  
 Les solutions tabulaires et multidimensionnelles sont créées à l'aide de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] et sont destinées aux projets Business Intelligence d'entreprise qui s'exécutent sur une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] autonome. Les deux solutions fournissent des bases de données d'analyse haute performance qui s'intègrent facilement aux rapports Excel Reporting Services, et à d'autres applications Business Intelligence fournies par Microsoft et par des tiers. Les deux solutions génèrent des bases de données autonomes qui peuvent être utilisées par toute application cliente prenant en charge Analysis Services.  
  
 D'un point de vue global, les différences entre les modèles tabulaires et multidimensionnels peuvent être caractérisées comme suit :  
  
-   Les solutions multidimensionnelles et d'exploration de données utilisent des constructions de modélisation OLAP (cubes et dimensions) et le stockage MOLAP, ROLAP ou HOLAP utilisant le disque comme stockage de données principal pour les données préagrégées.  
  
-   Les solutions tabulaires utilisent des constructions de modélisation relationnelle telles que des tables et des relations pour la modélisation des données, ainsi que le moteur d'analyse en mémoire pour le stockage et le calcul des données. La quasi-totalité des modèles sont stockés dans la mémoire RAM et sont souvent beaucoup plus rapides que leurs homologues multidimensionnels.  
  
 Pour les nouveaux projets, envisagez d'abord l'approche tabulaire. Il sera plus facile à concevoir, tester et déployer et fonctionnera mieux avec les applications Business Intelligence libre-service les plus récentes fournies par Microsoft.  
  
##  <a name="bkmk_ds"></a>Prise en charge des sources de données par type de solution  
 Les modèles multidimensionnels et tabulaires utilisent des données importées à partir de sources externes. La plupart des développeurs utilisent un entrepôt de données, conçu pour prendre en charge les structures de données de rapports, comme source de données principale d'un modèle. L'entrepôt de données est souvent basé sur un schéma en étoile ou en flocon, et SSIS est utilisé pour charger les données à partir de solutions OLTP dans l'entrepôt de données. La modélisation est plus simple quand vous utilisez un entrepôt de données comme source de données principale.  
  
|**Lien**|**Récapitulatif des options prises en charge**|  
|--------------|--------------------------------------|  
|[Sources de données prises en charge &#40;SSAS multidimensionnel&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md)|Les modèles multidimensionnels utilisent des données provenant de sources de données relationnelles.|  
|[Sources de données prises en charge &#40;&#41;tabulaire SSAS](tabular-models/data-sources-supported-ssas-tabular.md)|Les modèles tabulaires prennent en charge un grand nombre de sources de données, y compris les fichiers plats, les flux de données et les sources de données accessibles via des fournisseurs de données ODBC.|  
  
 Les deux approches de modélisation peuvent utiliser des données de plusieurs sources de données dans le même modèle.  
  
 Si votre solution demande de stocker les données de modèle en dehors du modèle dans la base de données relationnelle (technique utilisée quand la taille des données est particulièrement volumineuse), le type de source de données doit être une base de données relationnelle SQL Server. Le stockage ROLAP des modèles multidimensionnels et le DirectQuery des modèles tabulaires ont tous deux cette spécification.  
  
 **Taille des données**  
  
 Les solutions tabulaires et multidimensionnelles utilisent la compression des données, ce qui réduit la taille de la base de données Analysis Services par rapport à l'entrepôt de données à partir duquel vous importez les données. Étant donné que la compression réelle varie en fonction des caractéristiques des données sous-jacentes, il n'existe aucun moyen de connaître précisément la quantité d'espace disque et de mémoire requise par une solution après que les données ont été traitées et utilisées dans des requêtes. Une estimation utilisée par de nombreux développeurs Analysis Services est que le stockage principal d'une base de données multidimensionnelle sera environ équivalent à un tiers de la taille des données d'origine.  
  
 Les bases de données tabulaires peuvent parfois obtenir un taux de compression plus élevé, environ un dixième de la taille et ce, plus particulièrement si la plupart des données est importée depuis des tables de faits. Pour les bases de données tabulaires, la configuration requise pour la mémoire sera supérieure à la taille des données sur le disque en raison des structures de données supplémentaires qui sont créées lors du chargement de la base de données tabulaire dans la mémoire. Lors du chargement, la configuration requise pour le disque et la mémoire pour les deux types de solutions peut être augmentée à mesure qu'Analysis Services met en cache, stocke, analyse et interroge les données.  
  
 Pour certains projets, la configuration requise pour les données peut être si volumineuse qu'elle devient un facteur de choix entre les types de modèles. Si les données à charger représentent plusieurs téraoctets, une solution tabulaire ne répondra peut-être pas à vos besoins si la mémoire disponible n'est pas suffisante. Il existe une option de pagination qui place les données en mémoire sur disque ; cependant les très gros volumes de données sont mieux gérés dans des solutions multidimensionnelles. Les bases de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] les plus volumineuses en production aujourd'hui sont multidimensionnelles. Pour plus d'informations sur les options de pagination en mémoire pour les solutions tabulaires, consultez [Memory Properties](server-properties/memory-properties.md). Pour plus d'informations sur la mise à l'échelle d'une solution multidimensionnelle, consultez [Scale-Out Querying for Analysis Services with Read-Only Databases](https://go.microsoft.com/fwlink/?LinkId=251711).  
  
##  <a name="bkmk_models"></a>Fonctionnalités du modèle  
 Le tableau suivant résume la disponibilité des fonctionnalités au niveau du modèle. Si vous avez déjà installé Analysis Services, vous pouvez utiliser ces informations pour comprendre les possibilités offertes par le mode de serveur installé. Si vous êtes familiarisé avec les fonctionnalités de modèle dans Analysis Services et que les besoins de votre entreprise incluent une ou plusieurs de ces fonctionnalités, vous pouvez examiner cette liste pour vérifier que la fonctionnalité que vous voulez utiliser est disponible dans le type de modèle vous envisagez de créer.  
  
 Pour plus d'informations sur les fonctionnalités comparées par l'approche de modélisation, consultez l'article technique [Choosing a Tabular or Multidimensional Modeling Experience in SQL Server 2012 Analysis Services](https://go.microsoft.com/fwlink/?LinkId=251588) sur MSDN.  
  
> [!NOTE]  
>  La modélisation tabulaire est prise en charge dans des éditions spécifiques de SQL Server. Pour plus d'informations, consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
||||  
|-|-|-|  
||**Multidimensionnel**|**Tabulaire**|  
|Actions|[Oui](multidimensional-models/actions-in-multidimensional-models.md)|Non|  
|Objets d'agrégation|[Oui](multidimensional-models/designing-aggregations-analysis-services-multidimensional.md)|Non|  
|Mesures calculées|[Oui](multidimensional-models/create-calculated-members.md)|Oui|  
|Assemblys personnalisés|[Oui](multidimensional-models/multidimensional-model-assemblies-management.md)|Non|  
|Cumuls personnalisés|Oui|Non|  
|Distinct Count|[Oui](multidimensional-models/use-aggregate-functions.md)|Oui (via DAX) *|  
|Extraction|[Oui](multidimensional-models/actions-in-multidimensional-models.md)|Oui|  
|Hierarchies|[Oui](multidimensional-models/user-defined-hierarchies-create.md)|Oui|  
|Indicateurs de performance clés|[Oui](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|Oui|  
|Groupes de mesures liés|[Oui](multidimensional-models/linked-measure-groups.md)|Non|  
|Relations plusieurs-à-plusieurs|[Oui](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)|Non|  
|Hiérarchies parent-enfant|[Oui](multidimensional-models/parent-child-dimension.md)|Oui (via DAX)|  
|Partitions|[Oui](tabular-models/partitions-ssas-tabular.md)|  
|perspectives|[Oui](multidimensional-models/perspectives-in-multidimensional-models.md)|[Oui](tabular-models/partitions-ssas-tabular.md)|  
|Mesures semi-additives|[Oui](multidimensional-models/define-semiadditive-behavior.md)|Oui (via DAX)|  
|Translations|[Oui](multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|Non|  
|Hiérarchies définies par l'utilisateur|[Oui](multidimensional-models/user-defined-hierarchies-create.md)|Oui|  
|Écriture différée|[Oui](multidimensional-models/set-partition-writeback.md)|Non|  
  
 * Si votre solution doit prendre en charge un très grand nombre de nombres distincts (par exemple, plusieurs millions d’ID de client), envisagez d’abord le tabulaire. Elle est généralement plus performante dans ce cas. Consultez la section sur les calculs distincts dans le livre blanc, [Étude de cas Analysis Services : utilisation des modèles tabulaires dans des solutions commerciales à grande échelle](https://msdn.microsoft.com/library/dn751533.aspx).  
  
##  <a name="bkmk_modelsize"></a>Taille du modèle  
 La taille du modèle, en termes de nombre total d'objets, est identique par type de solution. Toutefois, les outils de conception utilisés pour générer chaque solution varient selon la façon dont ils s'adaptent au traitement d'un grand nombre d'objets. Il est plus facile de générer un modèle plus grand dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] , car il fournit davantage de capacités de création de schémas et de listes des objets par type dans l'Explorateur d'objets et dans l'Explorateur de solutions.  
  
 Les modèles très volumineux composés de plusieurs centaines de tables ou dimensions sont souvent générés par programme dans Visual Studio et non pas par les outils de conception. Pour plus d’informations sur le nombre maximal d’objets dans un modèle, consultez [spécifications de capacité maximale &#40;Analysis Services&#41;](multidimensional-models/olap-physical/maximum-capacity-specifications-analysis-services.md).  
  
##  <a name="bkmk_ext"></a>Programmabilité et expérience des développeurs  
 Pour les modèles tabulaires et multidimensionnels, il existe un modèle objet partagé pour les deux modalités. AMO et ADOMD.NET prennent en charge les deux modes. Aucune bibliothèque cliente n'a été révisée pour les constructions tabulaires. Par conséquent, vous devez bien comprendre la façon dont les constructions multidimensionnelles et tabulaires et les conventions d'affection de noms sont liées les unes aux autres. La première étape consiste à examiner l'exemple de programmation des objets AMO vers des objets tabulaires pour en savoir plus sur la programmation AMO dans un modèle tabulaire. Pour plus d'informations, téléchargez l'exemple disponible sur le [site Web Codeplex](https://go.microsoft.com/fwlink/?LinkID=221036).  
  
 Les solutions tabulaires ne prennent en charge qu'un seul fichier model.bim par solution, ce qui signifie que toutes les tâches doivent être effectuées dans un seul fichier. Les équipes de développement habituées à travailler avec plusieurs projets dans une seule solution devront peut-être modifier leur travail lors de la génération d'une solution tabulaire partagée.  
  
##  <a name="bkmk_lang"></a>Prise en charge des langages de requête et de script  
 Analysis Services inclut MDX, DMX, DAX, XML/A et ASSL. La prise en charge de ces langages varie légèrement suivant le type de modèle. Si les spécifications du langage de requête et de script sont un facteur important, consultez la liste suivante.  
  
-   Les bases de données model tabulaires prennent en charge les calculs DAX, les requêtes DAX et les requêtes MDX.  
  
-   Les bases de données model multidimensionnelles prennent en charge les calculs MDX, les requêtes MDX et ASSL.  
  
-   Les modèles d'exploration de données prennent en charge DMX et ASSL.  
  
-   PowerShell Analysis Services est pris en charge pour l'administration des serveurs et des bases de données. Le type de modèle (ou le mode serveur) n'est pas un facteur utilisant les applets de commande PowerShell.  
  
 Toutes les bases de données prennent en charge XML/A.  
  
##  <a name="bkmk_sec"></a>Prise en charge des fonctionnalités de sécurité  
 Toutes les solutions Analysis Services peuvent être sécurisées au niveau de la base de données. Les options de sécurité plus granulaires varient en fonction du mode. Si les paramètres de sécurité granulaires constituent un facteur important de votre solution, consultez la liste suivante pour vérifier que le niveau de sécurité que vous souhaitez est pris en charge dans le type de solution que vous voulez créer :  
  
-   Les bases de données model tabulaires peuvent utiliser la sécurité au niveau des lignes, à l'aide d'autorisations basées sur les rôles dans Analysis Services.  
  
-   Les bases de données model multidimensionnelles peuvent utiliser la sécurité au niveau des cellules et des dimensions, à l'aide d'autorisations basées sur les rôles dans Analysis Services.  
  
 Les modèles de données Excel peuvent être restaurés à un serveur en mode tabulaire. Une fois le fichier restauré, il est découplé de SharePoint (en supposant que vous l'avez restauré à partir d'un emplacement SharePoint), ce qui vous permet d'utiliser presque toutes les fonctionnalités de modélisation tabulaire, notamment la sécurité au niveau des lignes. La fonctionnalité de modélisation tabulaire que vous ne pouvez pas utiliser sur un classeur restauré est celle des tables liées.  
  
##  <a name="bkmk_designer"></a>Outils de conception  
 Les compétences et l'expertise technique concernant la modélisation des données peuvent varier considérablement suivant les utilisateurs qui sont chargés de créer des modèles analytiques. Si la connaissance des outils ou le savoir-faire des utilisateurs constituent un facteur important, comparez les expériences suivantes pour la création de modèles.  
  
|**Outil de modélisation**|**Mode d'utilisation**|  
|-----------------------|------------------|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|À utiliser pour créer des solutions tabulaires, multidimensionnelles et d'exploration de données. Cet environnement de création utilise le shell Visual Studio pour fournir des espaces de travail, des volets de propriétés et la navigation entre les objets. Les utilisateurs techniques qui utilisent déjà Visual Studio préfèreront très probablement cet outil pour créer des applications décisionnelles. Pour plus d'informations, consultez [Tools and applications used in Analysis Services](tools-and-applications-used-in-analysis-services.md) .|  
|Excel 2013 et versions ultérieures, avec le complément PowerPivot pour Excel|PowerPivot pour Excel est un outil utilisé pour modifier et améliorer les modèles de données Excel. Il possède un espace de travail d'application distinct qui s'ouvre dans Excel, mais utilise les mêmes métaphores visuelles (pages à onglets, disposition en grille et barre de formule) qu'Excel. Les utilisateurs qui maîtrisent parfaitement Excel préfèreront cet outil à [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Voir [Power Pivot : analyse et modélisation de données puissantes dans Excel](https://support.office.com/en-ie/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-d7b119ed-1b3b-4f23-b634-445ab141b59b).|  
  
##  <a name="bkmk_client"></a>Applications clientes et de création de rapports  
 Dans les versions précédentes, le choix du type de modèle avait un impact sur les applications clientes utilisables, mais cette caractéristique a diminué au fil du temps. Les approches tabulaire et multidimensionnelle prennent en charge de manière quasiment identique les applications clientes qui se connectent aux données Analysis Services. Le tableau suivant répertorie les applications clientes Microsoft pouvant être utilisées avec les modèles de données Analysis Services.  
  
|**Application**|**Description**|  
|---------------------|---------------------|  
|Rapports de tableau croisé dynamique Excel|Les fonctionnalités d'Excel sont identiques pour les modèles tabulaires et multidimensionnels, bien que l'écriture différée (une fonctionnalité d'Analysis Services implémentée par Excel) ne soit prise en charge que dans les modèles multidimensionnels.|  
|Rapports Reporting Services RDL|Les rapports RDL, créés dans le Générateur de rapports ou le Concepteur de rapports, peuvent utiliser n'importe quel modèle Analysis Services ainsi que les modèles de données Excel hébergés sur PowerPivot pour SharePoint.|  
|Tableaux de bord PerformancePoint|Dans SharePoint, les tableaux de bord PerformancePoint peuvent se connecter à toutes les bases de données Analysis Services, y compris les modèles de données Excel. Pour plus d'informations, consultez [Créer des connexions de données (PerformancePoint Services)](https://go.microsoft.com/fwlink/?linkdID=218155).|  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]dans les sites Office 365 ou Power BI|Modèles tabulaires uniquement.|  
|
  [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] dans SharePoint local|
  [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], en tant qu'application ClickOnce de SharePoint, peut utiliser un cube Analysis Services ou un modèle tabulaire.|  
  
##  <a name="bkmk_deploymentmode"></a>Modes de déploiement de serveur pour les solutions multidimensionnelles et tabulaires  
 Une instance d'Analysis Services est installée dans un des trois modes qui définissent le contexte opérationnel du serveur. Le mode de serveur que vous installez détermine le type de solutions qui peuvent être déployées sur ce serveur. Le stockage et l'architecture de mémoire sont les principales différences entre ces modes, mais ce ne sont pas les seules. Les trois modes serveur sont brièvement décrits dans le tableau suivant. Pour plus d’informations, consultez [Déterminer le mode serveur d’une instance Analysis Services](instances/determine-the-server-mode-of-an-analysis-services-instance.md).  
  
|Mode de déploiement|Description|  
|---------------------|-----------------|  
|0 - Mode multidimensionnel et d'exploration de données|Exécute les solutions multidimensionnelles et d'exploration de données que vous déployez sur une instance par défaut d'Analysis Services. Le mode de déploiement 0 est le mode par défaut pour une installation Analysis Services. Pour plus d'informations, consultez [Install Analysis Services in Multidimensional and Data Mining Mode](../../2014/sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md).|  
|1 - PowerPivot pour SharePoint|Pour l'accès au modèle de données Excel, Analysis Services est un composant interne de SharePoint. Analysis Services est installé en mode de déploiement 1 et accepte uniquement les requêtes d'Excel Services dans un environnement SharePoint. Pour plus d'informations, consultez [PowerPivot for SharePoint 2010 Installation](../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md).|  
|2- Mode tabulaire|Exécute les solutions tabulaires sur une instance autonome d'Analysis Services configurée pour le mode de déploiement 2. Pour plus d'informations, consultez [Install Analysis Services in Tabular Mode](instances/install-windows/install-analysis-services.md).|  
  
 Notez que les modèles de serveur ne sont pas interchangeables. Pendant l'installation, vous devez choisir un mode de fonctionnement du serveur. Vous devez installer plusieurs instances, une pour chaque mode de serveur, afin de prendre en charge toutes les charges de travail.  
  
##  <a name="bkmk_sharePoint"></a>Plateformes d’hébergement  
 Microsoft propose plusieurs méthodes pour l'hébergement des données, des applications, des rapports et de la collaboration. Dans cette section, nous abordons l'interopérabilité d'Analysis Services concernant chaque plateforme d'hébergement.  
  
|**Plateforme**|**Description**|  
|------------------|---------------------|  
|Microsoft Azure|Vous pouvez exécuter n'importe quelle version ou édition prise en charge d'Analysis Services sur une machine virtuelle Azure. Contrairement à la base de données SQL Azure, qui est un service sur Azure fournissant la plupart des fonctionnalités d'un moteur de base de données relationnelle local, Analysis Services n'a aucun équivalent sur Azure. L'installation, la configuration et l'exécution d'Analysis Services dans une machine virtuelle Azure constituent la seule option Azure.|  
|Office 365|Excel Online dans Office 365 prend en charge les connexions à distance aux modèles tabulaires et multidimensionnels qui s'exécutent localement.|  
|Sites Power BI dans Office 365|Dans un site Power BI, les rapports Power View peuvent se connecter aux modèles de données tabulaires qui s'exécutent localement.|  
|Sur des serveurs locaux (instances de SQL Server et SharePoint)|Un serveur de base de données local (autrement dit, une instance de SQL Server disposant d'Analysis Services) est toujours le moyen principal de mettre les données d'Analysis Services à la disposition des applications clientes et de rapports. Les solutions tabulaires, multidimensionnelles et d'exploration de données s'exécutent sur des instances Analysis Services sur un réseau sans dépendance SharePoint.<br /><br /> SQL Server s'intègre à SharePoint en ajoutant la prise en charge pour l'accès aux données PowerPivot et aux données tabulaires. L'investissement dans l'intégration SharePoint et SQL Server augmente lorsque vous optimisez le nombre de fonctionnalités utilisées dans chaque produit. Si vous disposez de SharePoint, installez SQL Server PowerPivot pour SharePoint pour permettre l'accès aux données PowerPivot et obtenir les fichiers de connexion .bism PowerPivot utilisés pour accéder aux bases de données tabulaires exécutées sur une instance Analysis Services externe sur un serveur réseau.<br /><br /> Si vous disposez de SharePoint et de SQL Server, vous pouvez prendre en charge la combinaison de services et d'applications suivante :<br /><br /> Modèles Analysis Services (tabulaires ou multidimensionnels)<br /><br /> Services SharePoint de niveau intermédiaire (Excel Services, Reporting Services dans SharePoint ou PerformancePoint Services)<br /><br /> Clients de navigateur ou clients riches (Excel) pour une analyse et une exploration approfondies des données.|  
  
##  <a name="bkmk_Next"></a>Étape suivante : générer une solution  
 Maintenant que vous avez des connaissances de base sur la comparaison des solutions, essayez les didacticiels suivants pour apprendre les étapes de création de chacune d'elles. Les liens suivants renvoient vers les didacticiels qui expliquent les étapes à suivre.  
  
-   Générez un modèle tabulaire à l’aide de la [modélisation tabulaire &#40;didacticiel Adventure Works &#41;](tabular-modeling-adventure-works-tutorial.md).  
  
-   Générez un modèle multidimensionnel à l’aide de la [modélisation multidimensionnelle &#40;didacticiel Adventure Works &#41;](multidimensional-modeling-adventure-works-tutorial.md).  
  
-   Générez un modèle d'exploration de données à l'aide de [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
-   Générez un modèle PowerPivot à l'aide du [Didacticiel PowerPivot pour Excel](https://go.microsoft.com/fwlink/?LinkId=251135).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des instances de Analysis Services](instances/analysis-services-instance-management.md)   
 [Nouveautés de Analysis Services et Business Intelligence](what-s-new-in-analysis-services.md)   
 [Nouveautés &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md)   
 [Nouveautés de PowerPivot](https://go.microsoft.com/fwlink/?LinkId=238141)   
 [Aide PowerPivot pour SQL Server 2012](https://go.microsoft.com/fwlink/?LinkID=220946)   
 [Connexion de modèle sémantique BI PowerPivot &#40;. BISM&#41;](power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)   
 [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)  
  
  
