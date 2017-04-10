---
title: "Comparaison des solutions tabulaires et multidimensionnelles (SSAS) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 76ee5e96-6a04-49af-a88e-cb5fe29f2e9a
caps.latest.revision: 49
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 47
---
# Comparaison des solutions tabulaires et multidimensionnelles (SSAS)
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] propose diverses approches pour la création d’un modèle sémantique Business Intelligence (BI) : multidimensionnel, tabulaire et PowerPivot.  
  
 Le fait d’avoir plusieurs approches offre une expérience de modélisation adaptée aux différents besoins des entreprises et des utilisateurs. Le modèle multidimensionnel est une technologie rodée reposant sur des normes ouvertes, adoptée par de nombreux éditeurs de logiciels d’aide à la décision (Business Intelligence ou BI), mais il peut être difficile à maîtriser. Le modèle tabulaire propose une approche de modélisation relationnelle que de nombreux développeurs jugent plus intuitive. Le modèle PowerPivot est encore plus simple, car il offre une modélisation visuelle des données dans Excel, avec prise en charge des serveurs fournie via SharePoint.  
  
 Tous les modèles sont déployés en tant que bases de données qui s’exécutent sur une instance d’Analysis Services, accessible aux outils clients à l’aide d’un ensemble de fournisseurs de données, et visualisable dans des rapports interactifs et statiques via Excel, Reporting Services, Power BI et des outils BI d’autres fournisseurs.  
  
 En raison de différences dans l’architecture de la mémoire et les métadonnées, les types de modèle ne sont pas interchangeables, même si vous pouvez procéder très facilement à une mise à niveau d’un modèle tabulaire 1050-1103 vers un modèle tabulaire 1200, et pouvez importer PowerPivot pour créer un modèle entièrement nouveau en tant que projet tabulaire.  
  
 Les solutions tabulaires et multidimensionnelles sont créées à l’aide de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] , et destinées à des projets BI d’entreprise s’exécutant sur une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] autonome. Les deux solutions fournissent des bases de données analytiques hautes performances qui s’intègrent aisément aux clients BI. Pourtant, chaque solution diffère dans la façon dont elle est créée, utilisée et déployée. L’essentiel de cette rubrique compare ces deux types afin que vous puissiez identifier l’approche qui vous convient.  
  
 Pour les nouveaux projets de développement, nous recommandons généralement le type tabulaire. Il est plus facile à concevoir, tester et déployer, et fonctionne mieux avec les applications BI et services cloud libre-service les plus récents de Microsoft.  
  
##  <a name="a-namebkmkoverviewa-overview-of-modeling-types"></a><a name="bkmk_overview"></a> Vue d’ensemble des types de modélisation  
 Vous découvrez Analysis Services ? Le tableau suivant énumère les différents modèles, résume l’approche et identifie le support de diffusion initial.  
  
||||  
|-|-|-|  
|**Type**|**Description de la modélisation**|**Diffusion**|  
|(Multidimensionnel)|Constructions de modélisation OLAP (cubes, dimensions, mesures).|SQL Server 2000 et versions ultérieures|  
|Tabulaire|Constructions de modélisation relationnelle (modèle, tables, colonnes).<br /><br /> En interne, les métadonnées sont héritées de constructions de modélisation OLAP (cubes, dimensions, mesures). Le code et les scripts utilisent des métadonnées OLAP.|SQL Server 2012 et versions ultérieures (niveaux de compatibilité 1050-1103) <sup>1</sup>|  
|Tabulaire dans SQL Server 2016|Constructions de modélisation relationnelle (modèle, tables, colonnes), articulées dans des définitions d’objet de métadonnées tabulaires sous forme de scripts et du code.|SQL Server 2016 (niveau de compatibilité 1200)|  
|Power Pivot|À l’origine un complément, désormais entièrement intégré dans Excel. Modélisation uniquement, sur une infrastructure tabulaire interne. Vous pouvez importer un modèle PowerPivot dans SSDT pour créer un modèle tabulaire s’exécutant sur une instance Analysis Services.|Via Excel et Power BI Desktop|  
  
 <sup>1</sup> Introduits dans SQL Server 2012, les niveaux de compatibilité sont importants dans la version actuelle, en raison du nouveau moteur de métadonnées tabulaires et de la prise en charge de fonctionnalités de scénario disponibles uniquement au niveau supérieur. Parmi les avancées remarquables figurent DirectQuery, les scripts et la programmabilité. Pour plus d'informations, consultez [What's New in Analysis Services](../analysis-services/what-s-new-in-analysis-services.md) .  
  
##  <a name="a-namebkmkmodelsa-model-features"></a><a name="bkmk_models"></a> Fonctionnalités de modèle  
  Le tableau suivant résume la disponibilité des fonctionnalités au niveau du modèle. Passez en revue cette liste pour vérifier que la fonctionnalité que vous voulez utiliser est disponible dans le type de modèle que vous prévoyez de créer.  
  
|||||  
|-|-|-|-|  
||(Multidimensionnel)|Tabulaire|Power Pivot|  
|Actions|Oui|Non|Non|  
|Aggregations|Oui|Non|Non|  
|Colonne calculée|Non|Oui|Oui|  
|Mesures calculées|Oui|Oui|Oui|  
|Tables calculées|Non|Oui <sup>1</sup>|Non|  
|Assemblys personnalisés|Oui|Non|Non|  
|Cumuls personnalisés|Oui|Non|Non|  
|Membre par défaut|Oui|Non|Non|  
|Dossiers d’affichage|Oui|Oui <sup>1</sup>|Non|  
|Distinct Count|Oui|Oui (via DAX)|Oui (via DAX)|  
|Extraction|Oui|Oui (les détail s'affichent dans une feuille de calcul distincte)|Oui|  
|Hierarchies|Oui|Oui|Oui|  
|Indicateurs de performance clés|Oui|Oui|Oui|  
|Objets liés|Oui|Oui (tables liées)|Non|  
|Relations plusieurs-à-plusieurs|Oui|Non (mais il existe des [filtres croisés bidirectionnels](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md) au niveau de compatibilité 1200)|Non|  
|Les jeux nommés|Oui|Non|Non|  
|Hiérarchies parent-enfant|Oui|Oui (via DAX)|Oui (via DAX)|  
|Partitions|Oui|Oui|Oui|  
|Perspectives|Oui|Oui|Oui|  
|Mesures semi-additives|Oui|Oui|Oui|  
|Translations|[Oui](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|Oui|[Oui](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)|  
|Hiérarchies définies par l'utilisateur|Oui|Oui|Oui|  
|Écriture différée|Oui|Non|Non|  
  
 <sup>1</sup> Pour plus d’informations sur les différences fonctionnelles au sein de la bande tabulaire, consultez [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
##  <a name="a-namebkmkdsa-data-considerations"></a><a name="bkmk_ds"></a> Considérations relatives aux données  
 Les modèles tabulaire et multidimensionnel utilisent des données importées à partir de sources externes. La quantité et le type de données que vous devez importer peuvent être des aspects essentiels à prendre en considération lors du choix du modèle le plus adapté à vos données.  
  
 **Compression**  
  
 Les solutions tabulaires et multidimensionnelles utilisent une compression de données qui réduit la taille de la base de données Analysis Services par rapport à l’entrepôt de données à partir duquel vous importez les données. Étant donné que la compression réelle varie en fonction des caractéristiques des données sous-jacentes, il n'existe aucun moyen de connaître précisément la quantité d'espace disque et de mémoire requise par une solution après que les données ont été traitées et utilisées dans des requêtes.  
  
 Une estimation utilisée par de nombreux développeurs Analysis Services est que le stockage principal d’une base de données multidimensionnelle équivaut environ à un tiers de la taille des données d’origine. Les bases de données tabulaires peuvent parfois obtenir un taux de compression plus élevé, environ un dixième de la taille et ce, plus particulièrement si la plupart des données est importée depuis des tables de faits.  
  
 **Taille du modèle et écart de ressource (en mémoire ou sur disque)**  
  
 La taille d’une base de données Analysis Services est limitée uniquement par les ressources disponibles pour l’exécuter. Le mode de stockage et le type de modèle déterminent également la taille que peut atteindre la base de données.  
  
 Les bases de données tabulaires s’exécutent soit en mémoire, soit en mode DirectQuery qui permet de décharger l’exécution des requêtes vers une base de données externe. Pour les analyses en mémoire tabulaire, la base de données est entièrement stockée en mémoire, ce qui signifie que vous devez disposer d’une mémoire suffisante pour charger non seulement toutes les données, mais aussi les structures de données supplémentaires créées pour prendre en charge les requêtes.  
  
 DirectQuery, revisité dans cette version, présente moins de restrictions et de meilleures performances qu’auparavant. Le fait de tirer parti de la base de données relationnelle principale pour le stockage et l’exécution des requêtes rend la génération d’un modèle tabulaire à grande échelle plus réalisable qu’auparavant.  
  
 Historiquement, les plus grandes bases de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en production sont multidimensionnelles, avec des charges de travail de traitement et de requête s’exécutant de façon indépendante sur du matériel dédié, chacune étant optimisée pour son propre usage.  Les bases de données tabulaires rattrapent rapidement leur retard, et de nouvelles avancées dans DirectQuery contribuent à combler l’écart encore davantage.  
  
 Pour le modèle multidimensionnel, un déchargement du stockage des données et de l’exécution des requêtes est disponible via ROLAP.   Un serveur de requêtes permet de mettre en cache des ensembles de lignes et de paginer mes ensembles caduques. L’utilisation efficace et équilibrée des ressources de mémoire et de disque guide souvent les clients vers des solutions multidimensionnelles.  
  
 Lors du chargement, la configuration requise pour le disque et la mémoire pour les deux types de solutions peut être augmentée à mesure qu'Analysis Services met en cache, stocke, analyse et interroge les données. Pour plus d’informations sur les options de pagination de mémoire, voir [Memory Properties](../analysis-services/server-properties/memory-properties.md). Pour en savoir plus sur l’échelle, voir [High availability and Scalability in Analysis Services](../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md).  
  
 PowerPivot pour Excel a une limite de taille de fichier artificielle de 2 gigaoctets, qui est imposée de façon à ce que les classeurs créés dans PowerPivot pour Excel puissent être téléchargés sur SharePoint, qui définit des limites maximales sur la taille de téléchargement des fichiers. Une des principales raisons de la migration d’un classeur PowerPivot vers une solution tabulaire sur une instance Analysis Services autonome réside est le contournement de cette limitation de taille de fichier. Pour plus d’informations sur la configuration de la taille maximale de téléchargement de fichiers, consultez [Configurer la taille maximale de téléchargement de fichiers &#40;PowerPivot pour SharePoint&#41;](../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).  
  
 **Sources de données prises en charge**  
  
 Les solutions multidimensionnelles peuvent importer des données à partir de sources de données relationnelles à l’aide de fournisseurs OLE DB natifs et gérés.  
  
 Les modèles tabulaires peuvent importer des données à partir de sources de données relationnelles, de flux de données et de certains formats de documents. Vous pouvez également utiliser des fournisseurs OLE DB pour ODBC avec des modèles tabulaires.  
  
 Pour afficher la liste des sources de données externes que vous pouvez importer dans chaque modèle, consultez les rubriques suivantes :  
  
-   [Sources de données prises en charge &#40;SSAS - Multidimensionnel&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
-   [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
##  <a name="a-namebkmklanga-query-and-scripting-language-support"></a><a name="bkmk_lang"></a> Prise en charge des langages de requêtes et de script  
 Analysis Services inclut MDX, DMX, DAX, XML/A, ASSL et TMSL. La prise en charge de ces langages peut varier selon le type de modèle. Si les spécifications du langage de requête et de script sont un facteur important, consultez la liste suivante.  
  
-   Les classeurs PowerPivot utilisent DAX pour les calculs, et DAX ou MDX pour les requêtes.  
  
-   Les bases de données model tabulaires prennent en charge les calculs DAX, les requêtes DAX et les requêtes MDX. Cela est vrai à tous les niveaux de compatibilité. Les langages de script sont ASSL (via XMLA) pour les niveaux de compatibilité 1050-1103, et TMSL (via XMLA) pour le niveau de compatibilité 1200.  
  
-   Les bases de données model multidimensionnelles prennent en charge les calculs MDX, les requêtes MDX et ASSL.  
  
-   Les modèles d'exploration de données prennent en charge DMX et ASSL.  
  
-   PowerShell Analysis Services est pris en charge pour les modèles et les bases de données tabulaires et multidimensionnels.  
  
 Toutes les bases de données prennent en charge XML/A. Pour plus d’informations, consultez [Référence du langage des requêtes et expressions &#40;Analysis Services&#41;](../Topic/Query%20and%20Expression%20Language%20Reference%20\(Analysis%20Services\).md) et [Guide du développeur (Analysis Services)](../analysis-services/analysis-services-developer-documentation.md).  
  
##  <a name="a-namebkmkseca-security-features"></a><a name="bkmk_sec"></a> Fonctionnalités de sécurité  
 Toutes les solutions Analysis Services peuvent être sécurisées au niveau de la base de données. Les options de sécurité plus granulaires varient en fonction du mode. Si les paramètres de sécurité granulaires constituent un facteur important de votre solution, consultez la liste suivante pour vérifier que le niveau de sécurité que vous souhaitez est pris en charge dans le type de solution que vous voulez créer :  
  
-   Les classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] sont sécurisés au niveau des fichiers à l’aide d’autorisations SharePoint.  
  
-   Les bases de données model tabulaires peuvent utiliser la sécurité au niveau des lignes, à l'aide d'autorisations basées sur les rôles dans Analysis Services.  
  
-   Les bases de données model multidimensionnelles peuvent utiliser la sécurité au niveau des cellules et des dimensions, à l'aide d'autorisations basées sur les rôles dans Analysis Services.  
  
 Les classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] peuvent être restaurés sur un serveur en mode tabulaire. Une fois le fichier restauré, il est découplé de SharePoint, ce qui vous permet d’utiliser toutes les fonctionnalités de modélisation tabulaire, dont la sécurité au niveau des lignes.  
  
##  <a name="a-namebkmkdesignera-design-tools"></a><a name="bkmk_designer"></a> Outils de conception  
 Les compétences et l'expertise technique concernant la modélisation des données peuvent varier considérablement suivant les utilisateurs qui sont chargés de créer des modèles analytiques. Si la connaissance des outils ou le savoir-faire des utilisateurs constituent un facteur important, comparez les expériences suivantes pour la création de modèles.  
  
|Outil de modélisation|Mode d'utilisation|  
|-------------------|--------------|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|À utiliser pour créer des solutions tabulaires, multidimensionnelles et d'exploration de données. Cet environnement de création utilise le shell Visual Studio pour fournir des espaces de travail, des volets de propriétés et la navigation entre les objets. Les utilisateurs techniques qui utilisent déjà Visual Studio préfèreront très probablement cet outil pour créer des applications décisionnelles.|  
|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour Excel|À utiliser pour créer un classeur [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] que vous déployez ultérieurement sur une batterie de serveurs SharePoint disposant d’une installation de [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint. [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour Excel offre un espace de travail d’application séparé qui s’ouvre sur Excel. Il utilise les mêmes métaphores visuelles (pages à onglets, disposition sous forme de grille et barre de formule) qu'Excel. Les utilisateurs qui maîtrisent parfaitement Excel préféreront cet outil sur [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].|  
  
##  <a name="a-namebkmkclienta-client-application-support"></a><a name="bkmk_client"></a> Prise en charge des applications clientes  
 Si vous utilisez Reporting Services, la disponibilité des fonctionnalités de rapport varie en fonction des éditions et des modes de serveur. Par conséquent, le type de rapport que vous voulez créer peut influencer le mode de serveur que vous choisissez d'installer.  
  
 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], le nouvel outil de conception de rapports Reporting Services qui s’exécute dans SharePoint, est disponible sur un serveur de rapports qui est déployé dans une batterie de serveurs SharePoint 2010. Le seul type de source de données utilisable avec ce rapport est une base de données de modèle tabulaire Analysis Services ou un classeur [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] . Cela signifie que vous devez avoir un serveur en mode tabulaire ou un serveur [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint pour héberger la source de données utilisée par ce type de rapport. Vous ne pouvez pas utiliser un modèle multidimensionnel comme source de données pour un rapport [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] . Vous devez créer une connexion du modèle sémantique BI [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ou d’une source de données partagée Reporting Services à utiliser comme source de données pour un rapport [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] .  
  
 Le Générateur de rapports et le Concepteur de rapports peuvent utiliser toute base de données Analysis Services, dont des classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] hébergés sur [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint.  
  
 Les rapports de tableau croisé dynamique Excel sont pris en charge par toutes les bases de données Analysis Services. Les fonctionnalités Excel sont identiques, que vous utilisiez une base de données tabulaire, une base de données multidimensionnelle ou un classeur [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , bien que l’écriture différée ne soit prise en charge que pour les bases de données multidimensionnelles.  
  
 Les tableaux de bord PerformancePoint peuvent se connecter à toutes les bases de données Analysis Services, y compris des classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] . Pour plus d'informations, consultez [Créer des connexions de données (PerformancePoint Services)](http://go.microsoft.com/fwlink/?linkdID=218155).  
  
##  <a name="a-namebkmkdeploymentmodea-server-deployment-modes-for-multidimensional-and-tabular-solutions"></a><a name="bkmk_deploymentmode"></a> Modes de déploiement serveur des solutions multidimensionnelles et tabulaires  
 Une instance d'Analysis Services est installée dans un des trois modes qui définissent le contexte opérationnel du serveur. Le mode de serveur que vous installez détermine le type de solutions qui peuvent être déployées sur ce serveur. Le stockage et l'architecture de mémoire sont les principales différences entre ces modes, mais ce ne sont pas les seules. Les trois modes serveur sont brièvement décrits dans le tableau suivant. Pour plus d’informations, consultez [Déterminer le mode serveur d’une instance Analysis Services](../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md).  
  
|Mode de déploiement|Description|  
|---------------------|-----------------|  
|0 - Mode multidimensionnel et d'exploration de données|Exécute les solutions multidimensionnelles et d'exploration de données que vous déployez sur une instance par défaut d'Analysis Services. Le mode de déploiement 0 est le mode par défaut pour une installation Analysis Services.|  
|1 - [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint|Pour l’accès aux données [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , Analysis Services est un composant interne d’une installation [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint. Analysis Services est installé en mode de déploiement 1, et utilisé exclusivement par les services [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] dans un environnement SharePoint.|  
|2- Mode tabulaire|Exécute les solutions tabulaires sur une instance autonome d'Analysis Services configurée pour le mode de déploiement 2.|  
  
 Pour plus d’informations, consultez [Installer Analysis Services](../analysis-services/instances/install-windows/install-analysis-services.md).  
  
##  <a name="a-namebkmksharepointa-sharepoint-requirements"></a><a name="bkmk_sharePoint"></a> Configuration requise de SharePoint  
 SQL Server s’intègre à SharePoint en ajoutant la prise en charge de l’accès aux données [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] et aux données tabulaires. L'investissement dans l'intégration SharePoint et SQL Server augmente lorsque vous optimisez le nombre de fonctionnalités utilisées dans chaque produit. Si vous disposez de SharePoint,vous pouvez installer SQL Server [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint pour permettre l’accès aux données [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] et obtenir les fichiers de connexion .bism [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] utilisés pour accéder aux bases de données tabulaires exécutées sur une instance Analysis Services externe sur un serveur réseau.  
  
 La fonctionnalité de création de rapports Power View, qui utilise des bases de données [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] et tabulaires comme source de données, est à la fois une fonctionnalité SharePoint fournie par SQL Server et une fonctionnalité intégrée d’Excel. Bien que les bases de données tabulaires s'exécutent sur une instance Analysis Services en dehors de SharePoint, les données sont consommées par les rapports Power View exécutés dans SharePoint.  
  
 Si vous n’utilisez pas SharePoint, vous pouvez toujours utiliser [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour Excel pour créer des classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] , mais cela ne vous procurera pas une expérience homogène de visualisation des données. Toute personne utilisant le classeur doit télécharger et consulter celui-ci dans Excel à l’aide du complément [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour Excel pour pouvoir interagir avec les données et les explorer à l’aide de segments, de filtres et de tableaux croisés dynamiques. Sinon, la visualisation du classeur est limitée aux données statiques telles qu'elles apparaissent lorsque vous ouvrez le classeur.  
  
 Les solutions tabulaires, multidimensionnelles et d'exploration de données s'exécutent sur des instances Analysis Services sur un réseau sans dépendance SharePoint.  
  
##  <a name="a-namebkmkexta-programmability-and-extensibility-support"></a><a name="bkmk_ext"></a> Prise en charge de la programmabilité et de l’extensibilité  
 S’il existe un support développeurs pour Power BI, il n’y en a pas pour les classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] . Si vous utilisez des classeurs [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], vous devez utiliser les applications clientes et serveur intégrées dans le cadre de votre solution. La programmation Excel et la programmation SharePoint sont les seules options.  
  
 Pour Power BI, voir [Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).  
  
 Les solutions tabulaires ne prennent en charge qu'un seul fichier model.bim par solution, ce qui signifie que toutes les tâches doivent être effectuées dans un seul fichier. Les équipes de développement habituées à travailler avec plusieurs projets dans une seule solution devront peut-être modifier leur travail lors de la génération d'une solution tabulaire partagée.  
  
 Les solutions tabulaires au niveau de compatibilité 1200 mappent à un nouveau modèle d’objet qui utilise des métadonnées tabulaires. Les modèles tabulaires plus anciens et tous les modèles multidimensionnels utilisent des métadonnées multidimensionnelles comme descripteurs. Nous vous recommandons de mettre à niveau des modèles tabulaires plus anciens vers le niveau de compatibilité 1200 afin de pouvoir utiliser des espaces de noms tabulaires dans AMO pour le code et les scripts personnalisés.  
  
 Pour plus d’informations, voir [Guide du développeur (Analysis Services)](https://msdn.microsoft.com/library/bb500153.aspx) .  
  
##  <a name="a-namebkmknexta-next-step-build-a-solution"></a><a name="bkmk_Next"></a> Étape suivante : créer une solution  
 Maintenant que vous avez des connaissances de base sur la comparaison des solutions, essayez les didacticiels suivants pour apprendre les étapes de création de chacune d'elles. Les liens suivants renvoient vers les didacticiels qui expliquent les étapes à suivre.  
  
-   Générez un modèle [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]. Consultez [Prise en main Power Pivot dans Microsoft Excel](https://support.office.com/article/Get-started-with-Power-Pivot-in-Microsoft-Excel-fdfcf944-7876-424a-8437-1a6c1043a80b).  
  
-   Générez un modèle tabulaire. Consultez [Modélisation tabulaire &#40;Didacticiel Adventure Works&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md).  
  
-   Générez un modèle multidimensionnel. Consultez [Modélisation multidimensionnelles &#40;didacticiel Adventure Works&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md).  
  
-   Générez un modèle d’exploration de données. Consultez [Didacticiel sur l’exploration de données de base](../Topic/Basic%20Data%20Mining%20Tutorial.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion d’instances Analysis Services](../analysis-services/instances/analysis-services-instance-management.md)   
 [Nouveautés d’Analysis Services](../analysis-services/what-s-new-in-analysis-services.md)     
 [Nouveautés dans PowerPivot](http://go.microsoft.com/fwlink/?LinkId=238141)   
 [Connexion de modèle sémantique BI Power Pivot &#40;.bism&#41;](../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)   
 [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)  
  
  