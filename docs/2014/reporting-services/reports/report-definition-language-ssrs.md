---
title: Rapport Definition Language (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Reporting Services, RDL
- Reporting Services, RDL
- RDL [Reporting Services], about Report Definition Language
- SSRS, RDL
- Report Definition Language, about Report Definition Language
- Report Definition Language
- RDL [Reporting Services]
- reports [Reporting Services], definitions
ms.assetid: b18b025e-f4bd-4744-8f86-0ac9fb967548
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b7c63e4850d17009992f8749c35d86534c0ee83
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188342"
---
# <a name="report-definition-language-ssrs"></a>Langage de définition de rapport (SSRS)
  Langage RDL (Report Definition) est une représentation XML d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] définition de rapport. Une définition de rapport contient des informations de récupération et la disposition d’un rapport. RDL se compose d’éléments XML qui correspondent à une grammaire XML créée pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Vous pouvez ajouter vos propres fonctions personnalisées pour les valeurs d’élément de rapport contrôle, des styles et mise en forme en accédant à des assemblys de code dans les fichiers de définition de rapport.  
  
 Le langage RDL favorise l’interopérabilité des produits de création de rapports commerciaux en définissant un schéma commun qui permet l’échange de définitions de rapport. N’importe quel protocole ou une interface de programmation qui fonctionnent avec XML peut être utilisé avec le langage RDL. RDL est :  
  
-   Un schéma XML pour les définitions de rapport.  
  
-   Format d’échange pour les entreprises et les tiers.  
  
-   Un schéma extensible et ouvert qui prend en charge des espaces de noms supplémentaires et des éléments personnalisés.  
  
##  <a name="bkmk_RDL_Specifications"></a> Spécifications RDL  
 Pour télécharger les caractéristiques des versions de schéma spécifiques, consultez [spécification de langage de définition de rapport](https://go.microsoft.com/fwlink/?linkid=116865).  
  
##  <a name="bkmk_RDL_XML_Schema_Definition"></a> Définition de schéma XML RDL  
 Un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fichier de langage RDL (Report Definition) est validé à l’aide d’un fichier de définition de schéma XML (XSD). Le schéma définit les règles pour où les éléments RDL peuvent se trouver dans un fichier .rdl. Un élément inclut son type de données et de la cardinalité, autrement dit, le nombre d’occurrences autorisées. Un élément peut être simple ou complexe. Un élément simple n’a pas d’attributs ou éléments enfants. Un élément complexe a des enfants et éventuellement des attributs.  
  
 Par exemple, le schéma inclut l’élément RDL `ReportParameters`, qui est le type complex `ReportParametersType`. Par convention, un type complexe pour un élément est le nom de l’élément de suivi par le mot `Type`. Un `ReportParameters` élément peut être contenu par le `Report` (un type complex) de l’élément et peut contenir `ReportParameter` éléments. Un `ReportParameterType` est un type simple qui ne peut avoir une des valeurs suivantes : `Boolean`, `DateTime`, `Integer`, `Float`, ou `String`. Pour plus d’informations sur les types de données de schéma XML, consultez [XML Schema Part 2 : Types de données deuxième édition](https://go.microsoft.com/fwlink/?linkid=4871).  
  
 Le XSD RDL est disponible dans le fichier ReportDefinition.xsd, situé dans le dossier Extras sur le CD-ROM du produit. Il est également disponible sur le serveur de rapports via l’URL suivante : http://servername/reportserver/reportdefinition.xsd.  
  
##  <a name="bkmk_Creating_RDL"></a> Création de RDL  
 En raison de la nature ouverte et extensible de RDL, les divers outils et applications qui génèrent le langage RDL selon son schéma XML peut être généré.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit plusieurs outils pour créer les fichiers RDL. Pour plus d’informations, consultez [outils de Reporting Services](../tools/reporting-services-tools.md).  
  
 Une des méthodes plus simples à générer le langage RDL à partir d’une application consiste à utiliser le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes de la <xref:System.Xml> espace de noms et <xref:System.Linq> espace de noms. Une classe en particulier, le **XmlTextWriter** de classe, peut être utilisé pour l’écriture du langage RDL. Avec **XmlTextWriter**, vous pouvez générer une définition de rapport complète à partir du début à la fin dans les [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] application. Les développeurs peuvent également étendre le langage RDL en ajoutant des éléments de rapport personnalisés avec des propriétés personnalisées. Pour plus d’informations sur la **XmlTextWriter** classe et le <xref:System.Xml> espace de noms, consultez le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Guide du développeur. Pour plus d’informations sur la requête LINQ (Language Integrated), recherchez « LINQ to XML » sur MSDN.  
  
 L’extension de fichier standard pour les fichiers de définition de rapport est .rdl. Vous pouvez également développer des fichiers de définition de rapport client qui portent l’extension .rdlc. Le type MIME pour les deux extensions est text/xml. Pour plus d’informations sur les rapports, consultez [rapports Reporting Services &#40;SSRS&#41;](reporting-services-reports-ssrs.md).  
  
##  <a name="bkmk_RDL_Types"></a> Types RDL  
 Le tableau suivant répertorie les types utilisés dans les attributs et éléments RDL.  
  
|Type|Description|  
|----------|-----------------|  
|`Binary`|Une propriété avec une base-64 codé valeur binaire.|  
|`Boolean`|Une propriété avec `true` ou `false` comme valeur de l’objet. Sauf indication contraire, la valeur d’un objet Boolean facultatif omis est `False`.|  
|`Date`|Une propriété avec une valeur de date ou date/heure entièrement spécifiée au format de date ISO8601 : AAAA-MM-JJ [THH [ : SS [. S]]].|  
|`Enum`|Une propriété avec une valeur de texte de chaîne qui doit être une liste de valeurs désignées.|  
|`Float`|Une propriété avec une valeur float. Un point (.) est utilisé comme séparateur décimal facultatif.|  
|`Integer`|Une propriété avec une valeur entière (int32).|  
|`Language`|Une propriété avec une valeur de texte qui contient un code de langue et culture, tel que « en-us » pour l’anglais américain. La valeur doit être une langue spécifique ou une langue neutre pour laquelle une langue par défaut est définie dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].|  
|`Name`|Une propriété avec une valeur de chaîne de texte. Noms doivent être uniques au sein de l’espace de noms de l’élément. Si non spécifié, l’espace de noms pour un élément est la plus intérieure contenant l’objet qui porte un nom.|  
|`NormalizedString`|Une propriété avec une valeur de texte de chaîne qui a été normalisée.|  
|`Size`|Un élément de taille doit contenir un nombre (avec une virgule comme séparateur décimal facultatif). Le nombre doit être suivi d’un indicateur pour une unité de longueur CSS par exemple, cm, mm, in, pt ou pc. Un espace entre le nombre et l’indicateur est facultatif. Pour plus d’informations sur les indicateurs de taille, consultez [CSS Length Units Reference](https://www.w3schools.com/CSSref/css_units.asp).<br /><br /> Dans le langage RDL, la valeur maximale pour `Size` est 160 po. La taille minimale est 0 po.|  
|`String`|Une propriété avec une valeur de chaîne de texte.|  
|`UnsignedInt`|Propriété dont la valeur entière non signée (uint32).|  
|`Variant`|Une propriété avec n’importe quel type XML simple.|  
  
##  <a name="bkmk_RDL_Data_Types"></a> Types de données RDL  
 L’énumération DataType définit le type de données d’un attribut, une expression ou un paramètre dans RDL. Le tableau suivant présente le common language runtime (CLR) données est types correspondent aux types de données RDL.  
  
|**CLR Type(s)**|**Type de données correspondant**|  
|-----------------------|---------------------------------|  
|Booléen|Booléen|  
|DateTime, DateTimeOffset|DateTime|  
|Int16, Int32, UInt16, Byte, SByte|Entier|  
|Single, Double|Float|  
|String, Char, GUID, Timespan|Chaîne|  
  
## <a name="see-also"></a>Voir aussi  
 [Rechercher la Version de schéma de définition de rapport &#40;SSRS&#41;](find-the-report-definition-schema-version-ssrs.md)   
 [Utilisation d’assemblys personnalisés avec des rapports](../custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Éléments de rapport personnalisés](../custom-report-items/custom-report-items.md)  
  
  
