---
title: Fonctionnalités des rapports d’accès prises en charge (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], Access reports
- functions [Reporting Services]
- controls [Reporting Services]
- Access reports [Reporting Services]
- properties [Reporting Services], Access reports
- importing reports
- modules [Reporting Services]
ms.assetid: 7ffec331-6365-4c13-8e58-b77a48cffb44
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9088ab3e90b4fb341cc8125e45d498783953039d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100577"
---
# <a name="supported-access-report-features-ssrs"></a>Fonctionnalités des états Access prises en charge (SSRS)
  Lorsque vous importez un rapport dans le Concepteur de rapports, le processus d'importation convertit le rapport d'Access [!INCLUDE[msCoName](../includes/msconame-md.md)] en un fichier RDL (Report Definition Language) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge plusieurs fonctionnalités d'Access ; toutefois, puisqu'il existe des différences entre Access et [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], certains éléments sont légèrement modifiés ou ne sont pas pris en charge. Cette rubrique décrit comment les fonctionnalités des états Access sont converties en mode RDL.  
  
## <a name="importing-access-reports"></a>Importation d'états Access  
 Certaines requêtes contiennent du code spécifique à Access. Ce code Access n'est pas importé avec l'état. De plus, si une requête contient des chaînes incorporées, l'état risque de ne pas s'importer correctement. Pour résoudre ce problème, remplacez les chaînes par un code de caractère. Par exemple, remplacez le caractère virgule (,) par CHAR(34).  
  
 Le processus d’importation ne passe pas correctement le point-virgule (;) ou les caractères de balisage XML (\<, >, etc.) dans les informations de chaîne de connexion. Si une chaîne de connexion contient un point-virgule ou un caractère de balise XML, vous devez définir le mot de passe manuellement dans le nouveau rapport après l'importation de l'état.  
  
 Le processus d'importation n'importe pas les paramètres de connexion ou de délais d'expiration généraux dans la chaîne de connexion. Il vous faudra peut-être régler ces paramètres après l'importation.  
  
 Si vous importez un état dont la requête contient des paramètres, cette requête ne sera pas convertie lors de l'importation de l'état. Pour importer la requête avec l'état, remplacez temporairement les paramètres de la requête dans l'état Access par des valeurs statiques, puis remplacez-les par les paramètres de la requête après l'importation de l'état.  
  
## <a name="page-layout"></a>Mise en page  
 La présentation de page dans Access n'est pas la même que dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Access organise les éléments de la page à l'aide de « bandes », c'est-à-dire des sections réparties verticalement sur la page. Ces sections peuvent inclure l'en-tête du rapport, son pied de page, l'en-tête de la page, son pied de page, les groupes et des détails. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] propose une mise en page plus souple. Les régions de données permettent le regroupement et l'affichage de détails. Vous pouvez placer plusieurs régions de données n'importe où dans le corps du rapport et même côte à côte. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclut également un en-tête et un pied de page sous forme de bande, semblable à l'en-tête et au pied de page dans Access.  
  
 Lorsqu'un état est importé à partir d'Access dans le Concepteur de rapports, l'en-tête et le pied de page de l'état Access sont convertis en en-tête et pied de page dans le rapport [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Les groupes et les détails sont convertis en région de données de type liste. L'en-tête et le pied de page de l'état sont placés dans le corps du rapport, et non plus dans une « bande » séparée. Ceci peut résulter en une organisation des éléments légèrement différente de celle trouvée dans l'état Access.  
  
> [!NOTE]  
>  Dans certains états Access, des éléments qui doivent s'afficher côte à côte risquent de se chevaucher. Lorsque l'état est importé à l'aide du Générateur de rapports, ce chevauchement n'est pas corrigé et risque de produire des résultats inattendus à l'exécution du rapport.  
  
## <a name="data-sources"></a>Sources de données  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les sources de données OLE DB, telles que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si vous importez des états d'un fichier de projet Access (.adp), la chaîne de connexion de la source de données est récupérée de la chaîne de connexion dans le fichier .adp. Si vous importez des états d'une base de données Access (.mdb ou .accdb), il est possible que la chaîne de connexion pointe sur la base de données Access et que vous deviez la corriger après l'importation des états. Si la source de données de l'état Access est une requête, les informations de la requête sont stockées sans modification dans le fichier RDL. Si la source de données de l'état Access est une table, le processus de conversion crée une requête basée sur le nom de la table et sur les champs de cette table.  
  
## <a name="reports-with-custom-modules"></a>Rapports avec modules personnalisés  
 Si du code personnalisé [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] est contenu dans des modules, il n’est pas converti. Si Concepteur de rapports rencontre du code pendant le processus d’importation, un avertissement est généré et affiché dans la fenêtre **liste des tâches** .  
  
## <a name="report-controls"></a>Contrôles des états  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les contrôles Access suivants et les inclut dans les définitions de rapports converties.  
  
|||||  
|-|-|-|-|  
|Image|Etiquette|Lignes|Rectangle|  
|Sous-formulaire|Sous-état<br /><br /> **Remarque** Lorsqu’un contrôle de sous-rapport est converti dans le rapport principal, le sous-rapport lui-même est converti séparément.|TextBox||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les contrôles suivants :  
  
|||||  
|-|-|-|-|  
|BoundObjectFrame|Case à cocher|ComboBox|Bouton de commande|  
|Contrôle personnalisé|ListBox|Cadre d'objet|Bouton d'option|  
|TabControl|Bouton bascule|||  
  
 Si Concepteur de rapports rencontre l’un de ces contrôles pendant le processus d’importation, un avertissement est généré et affiché dans la fenêtre **liste des tâches** .  
  
 Les autres contrôles comme ActiveX et Office Web Components ne sont pas importés. Par exemple, si un état Access contient un contrôle de graphique Office Web Components, il n'est pas converti lors de l'importation de l'état.  
  
## <a name="report-properties"></a>Propriétés des états  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les propriétés ci-dessous, qui sont accessibles à partir de l'interface utilisateur d'Access. Les propriétés disponibles uniquement dans le code ne sont pas prises en charge et ne sont pas présentées dans cette liste.  
  
|||||  
|-|-|-|-|  
|CouleurFond|StyleFond|BorderColor|BorderStyle|  
|BorderWidth|BottomMargin|AutoExtensible (zone de texte)|AutoRéductible (zone de texte)|  
|Caption|Gras|Italique|FontName|  
|FontSize|Souligné|FontWeight|SautPage|  
|CouleurTexte|Hauteur|HideDuplicates|Hyperlink|  
|EstLienHypertexte|EstVisible|SectionInsécable (groupe)|Gauche|  
|LeftMargin|Inclinaison|Interligne|ChampsFils|  
|ChampsPères|NvLigOuCol|PageFooter|PageHeader|  
|Pages|Photo|MosaïqueImages (rapport)|SensLecture|  
|RépéterSection|RightMargin|RunningSum|SizeMode|  
|TextAlign|TOP|TopMargin|Largeur|  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les propriétés ci-dessous, qui sont accessibles à partir de l'interface utilisateur d'Access.  
  
|||||  
|-|-|-|-|  
|CanGrow (section)|CanShrink (section)|DecimalPlaces|FastLaserPrinting|  
|Filtrer|FiltreActif|Format|FormatConditions|  
|GroupeInsécable|SectionInsécable (section)|FormatNumérotation|Orientation|  
|PaletteCouleurs|SourcePalette|AlignementImage|PagesImages|  
|ModeAffichageImage|MosaïqueImages (image)|BarreDéfilement|Apparence|  
|Vertical||||  
  
## <a name="grouping"></a>Regroupement  
 Access définit un niveau de groupe à l'aide d'une combinaison de trois propriétés : l'expression de groupe, la propriété `GroupOn` et la propriété `GroupInterval`. Un groupe qui n'a pas d'en-tête ou de pied de groupe est fusionné avec le groupe qu'il contient. Si le groupe ne contient pas un autre groupe, un tri est appliqué à la section Détails et le groupe est ignoré.  
  
## <a name="expressions"></a>Expressions  
 Access utilise des expressions pour spécifier des valeurs qui apparaissent dans des zones de texte. Access utilise [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] comme langage pour ses expressions en plus de certaines fonctions d'agrégation. Le Concepteur de rapports convertit ces expressions Access en expressions de rapport.  
  
### <a name="functions"></a>Fonctions  
 Les définitions de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] utilisent [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET comme langage d'expression natif, tandis qu'Access 2002 utilise Visual Basic. Les listes suivantes décrivent les fonctions prises en charge par [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
#### <a name="array-functions"></a>Fonctions de tableau  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions de tableau suivantes :  
  
-   LBound  
  
-   UBound  
  
#### <a name="conversion-functions"></a>Fonctions de conversion  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions de conversion suivantes :  
  
|||||  
|-|-|-|-|  
|Asc|CBool|CByte|CMonnaie|  
|CDate|CDbl|CDec|Chr|  
|Caract$|CEnt|CLong|CSmpl|  
|CChaîne|CVar|CVDate|Format|  
|FormatCurrency|FormatDateTime|FormatNumber|FormatPercent|  
|Hex|Hex$|Nz|Oct|  
|Oct$|NumChaîne|Str$|ConvChaîne|  
|Val||||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les fonctions de conversion suivantes :  
  
-   GUIDFromString  
  
-   StringFromGUID  
  
#### <a name="database-functions"></a>Fonctions de base de données  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions de base de données suivantes :  
  
|||||  
|-|-|-|-|  
|CreateReport|GetObject|HyperlinkPart|Partition|  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les fonctions de base de données suivantes :  
  
|||||  
|-|-|-|-|  
|CodeDb|CreateControl|CreateForm|CreateGroupLevel|  
|CreateObject|CreateReportControl|CurrentDb|Utilisateur en cours|  
|DeleteControl|DeleteReportControl|Eval|IMEStatus|  
|SysCmd||||  
  
#### <a name="datetime-functions"></a>Fonctions de date et d'heure  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions de date et d’heure suivantes :  
  
|||||  
|-|-|-|-|  
|Date|Date$|AjDate|DiffDate|  
|PartDate|SérieDate|ValDate|jour|  
|Heure|Minute|Month|MonthName|  
|maintenant|Seconde|Heure|Temps$|  
|Minuterie|SérieHeure|VHeure|Jour de la semaine|  
|WeekdayName|Year|||  
  
#### <a name="ddeole-functions"></a>Fonctions DDE/OLE  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les fonctions DDE/OLE suivantes :  
  
|||||  
|-|-|-|-|  
|DDE|DDEIntitate|DDERequest|DDESend|  
|LoadPicture||||  
  
#### <a name="domain-aggregate-functions"></a>Fonctions d'agrégation de domaines  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les fonctions d’agrégation de domaines suivantes :  
  
|||||  
|-|-|-|-|  
|MoyDom|CpteDom|PremDom|DernDom|  
|RechDom|MaxDom|DMin|DStDev|  
|DStDevP|DSum|DVar|DVarP|  
  
#### <a name="error-handling-functions"></a>Fonctions de gestion d'erreur  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions de gestion d'erreur suivantes :  
  
|||||  
|-|-|-|-|  
|Err|Error|Error$|IsError|  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge la fonction de gestion d'erreur suivante :  
  
-   CVErr  
  
#### <a name="financial-functions"></a>Fonctions financières  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions financières suivantes :  
  
|||||  
|-|-|-|-|  
|DDB|VC|IPmt|IRR|  
|MIRR|NPer|NPV|Vpm|  
|PPmt|PV|Tarif|AmorLin|  
|SYD||||  
  
#### <a name="interaction-functions"></a>Fonctions d'interaction  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions d’interaction suivantes :  
  
|||||  
|-|-|-|-|  
|Commande|Command$|RéperCour|RéperCour$|  
|DeleteSetting|Réper|Réper$|Environ|  
|Environ$|EOF|FileAttr|DateHeureFich|  
|LongFich|FreeFile|LireTousParam|LireAttr|  
|GetSetting|Loc|LOF|RVBC|  
|RGB|SaveSetting|Seek|SetAttr|  
|Shell|Spc|Onglet||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les fonctions d’interaction suivantes :  
  
|||||  
|-|-|-|-|  
|DoEvents|Dans|Entrée|Input$|  
  
#### <a name="inspection-functions"></a>Fonctions d'inspection  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions d’inspection suivantes :  
  
|||||  
|-|-|-|-|  
|IsArray|IsDate|IsEmpty|IsError|  
|IsNull|IsNumeric|IsObject|TypeName|  
|VarType||||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge la fonction d’inspection suivante :  
  
-   IsMissing  
  
#### <a name="math-functions"></a>Fonctions mathématiques  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions mathématiques suivantes :  
  
|||||  
|-|-|-|-|  
|Abs|Atn|Cos|Exp|  
|Fix|Int|Journal|Aléat|  
|Round|Sgn|Sin|Racine|  
|Tan||||  
  
#### <a name="message-functions"></a>Fonctions de message  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ne prend pas en charge les fonctions de message suivantes :  
  
|||||  
|-|-|-|-|  
|InputBox|InputBox$|MsgBox||  
  
#### <a name="program-flow-functions"></a>Fonctions de déroulement de programme  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions de déroulement de programme suivantes :  
  
|||||  
|-|-|-|-|  
|Choose|IIf|Commutateur||  
  
#### <a name="sql-aggregate-functions"></a>Fonctions d'agrégation SQL  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions d'agrégation SQL suivantes :  
  
|||||  
|-|-|-|-|  
|Avg|Count|Max|Min|  
|StDev|StDevP|SUM|Var|  
|VarP||||  
  
#### <a name="text-functions"></a>Fonctions de texte  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge les fonctions de texte suivantes :  
  
|||||  
|-|-|-|-|  
|Format|Format$|InStr|InStrRev|  
|Minuscule|Minuscule$|Gauche|Gauche$|  
|NbCar|SupprGauche|SupprGauche$|ExtracChaîne|  
|ExtracChaîne$|Replace|Right|Droite$|  
|SupprDroite|Espace|Espace$|CompChaîne|  
|ConvChaîne|String|Chaîne$|StrReverse|  
|SupprEspace|Trim$|UCase|UCase$|  
  
### <a name="constants"></a>Constantes  
 Access ne prend pas en charge les constantes spéciales [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] (par exemple `vbTrue`) dans les expressions. Aucune conversion n'est donc nécessaire. Il existe toutefois une exception : le mot clé `Null` est converti en `System.DbNull.Value`.  
  
### <a name="parameters"></a>Paramètres  
 Au cours du processus d'importation, le Générateur de rapports analyse chaque expression contenue dans les états à la recherche des variables qui ne correspondent pas à des noms de champs ou de contrôles. Ces variables sont ajoutées aux paramètres du rapport.  
  
 Le type de données des paramètres des procédures stockées est toujours importé en tant que chaîne. Après l'importation de l'état, vous devez modifier manuellement le paramètre pour utiliser le type de données correct.  
  
### <a name="object-names"></a>Noms d'objets  
 Contrairement à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], Access accepte que les champs aient le même nom que les contrôles. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 6.0 autorise les espaces dans les noms de variables, contrairement à Visual Basic .NET. Le processus d'importation remplace les noms de tels objets par des noms valides et attribue des noms uniques si plusieurs objets portent le même nom. Chaque expression est analysée et les noms des variables qui correspondent à des objets renommés sont remplacés par les nouveaux noms.  
  
## <a name="rectangles-and-containment"></a>Rectangles et relation contenant-contenu  
 Dans une définition de rapport [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], les rectangles peuvent contenir d'autres éléments de rapport. Tout rectangle plus large qu'un élément de rapport, et qui recouvre plus de 90 % de sa surface, devient le conteneur de cet élément de rapport.  
  
## <a name="bitmaps"></a>Images bitmap  
 Toutes les images bitmap qui sont incorporées dans un état sont converties au format .bmp lorsque l'état est importé, quel que soit leur format d'origine. Par exemple, si votre état inclut des fichiers .jpg et .gif, les ressources résultantes importées dans le rapport sont des fichiers .bmp. Les images bitmap sont stockées sous forme d'images incorporées dans le rapport. Pour plus d’informations sur les images incorporées, consultez [images &#40;générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md).  
  
## <a name="other-considerations"></a>Autres considérations  
 Outre les éléments précédemment cités, les informations qui suivent s'appliquent aux états importés à partir d'Access :  
  
-   La mise en forme conditionnelle n'est pas convertie.  
  
-   Le champ de description dans les propriétés d'état dans Access n'est pas converti.  
  
  
