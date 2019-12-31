---
title: XML, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.f1
helpviewer_keywords:
- XML [Integration Services]
- XML task [Integration Services]
ms.assetid: 9f761846-390e-46d5-9db7-858943d40849
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e89f4835b95b1fe497df32ad9f773be84ccb161b
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75232728"
---
# <a name="xml-task"></a>Tâche XML
  La tâche XML est utilisée pour travailler avec des données XML. À l'aide de cette tâche, un package peut extraire des documents XML, appliquer des opérations aux documents en utilisant des feuilles de style XSLT (Extensible Stylesheet Language Transformations) et des expressions XPath, fusionner plusieurs documents, ou bien valider, comparer et enregistrer les documents mis à jour dans des fichiers et des variables.  
  
 Cette tâche permet à un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de modifier de manière dynamique des documents XML au moment de l'exécution. Vous pouvez utiliser la tâche XML pour :  
  
-   remettre en forme un document XML. Cette tâche peut ainsi accéder à un rapport se trouvant dans un fichier XML et appliquer de manière dynamique une feuille de style XSLT afin de personnaliser la présentation du document ;  
  
-   sélectionner des sections d'un document XML. Cette tâche peut ainsi accéder à un rapport se trouvant dans un fichier XML et appliquer de manière dynamique une expression XPath afin de sélectionner une section du document. Cette opération peut également permettre d'obtenir et de traiter des valeurs dans un document ;  
  
-   fusionner des documents provenant de différentes sources. Cette tâche peut par exemple télécharger des rapports à partir de sources multiples et les fusionner de manière dynamique dans un document XML global unique.  
  
-   valider un document XML et éventuellement obtenir une sortie d’erreur détaillée. Pour plus d’informations, consultez [Validate XML with the XML Task](xml-task.md).  
  
 Vous pouvez inclure des données XML dans un flux de données en utilisant une source XML pour extraire des valeurs d'un document XML. Pour plus d'informations, consultez [XML Source](../data-flow/xml-source.md).  
  
## <a name="xml-operations"></a>Opérations XML  
 La première action de la tâche XML consiste à extraire un document XML spécifique. Cette action est intégrée à la tâche XML et est effectuée automatiquement. Le document XML récupéré est utilisé comme source de données de l'opération réalisée par la tâche XML.  
  
 Les opérations XML Diff, Merge et Patch requièrent deux opérandes. Le premier opérande spécifie le document XML source. Le second opérande spécifie également un document XML, dont le contenu dépend de ce dont l'opération a besoin. Par exemple, l'opération Diff compare deux documents. Le second opérande spécifie donc un autre document XML similaire auquel le document XML source est comparé.  
  
 La tâche XML peut utiliser une variable ou un gestionnaire de connexions de fichiers comme source ou inclure les données XML dans une propriété de tâche.  
  
 Si la source est une variable, la variable spécifiée contient le chemin d'accès du document XML.  
  
 Si la source est un gestionnaire de connexions de fichiers, ce gestionnaire fournit les informations sources. Le gestionnaire de connexions de fichiers est configuré séparément de la tâche XML et est référencé dans la tâche XML. La chaîne de connexion du gestionnaire de connexions de fichiers spécifie le chemin d'accès du fichier XML. Pour plus d’informations, consultez [Gestionnaire de connexions de fichiers](../connection-manager/file-connection-manager.md).  
  
 La tâche XML peut être configurée pour enregistrer les résultats de l'opération dans une variable ou un fichier. En cas d'enregistrement dans un fichier, la tâche XML utilise un gestionnaire de connexions de fichiers pour accéder au fichier. Vous pouvez également enregistrer les résultats du Diffgram généré par l'opération Diff dans des fichiers et des variables.  
  
## <a name="predefined-xml-operations"></a>Opérations XML prédéfinies  
 La tâche XML comprend un ensemble prédéfini d'opérations permettant de travailler avec des documents XML. Le tableau suivant décrit ces opérations.  
  
|Opération|Description|  
|---------------|-----------------|  
|Diff|Permet de comparer deux documents XML. Si le document XML source est utilisé comme document de base, l'opération Diff la compare à un second document XML, détecte leurs différences et écrit ces différences dans un document XML Diffgram. Cette opération inclut des propriétés permettant de personnaliser la comparaison.|  
|Fusionner|Permet de fusionner deux documents XML. Si le document XML source est utilisé comme document de base, l'opération Merge ajoute le contenu d'un second document dans le document de base. Cette opération peut spécifier un emplacement de fusion dans le document de base.|  
|Correctif|Applique la sortie de l'opération Diff, appelée document Diffgram, à un document XML afin de créer un document parent qui inclut le contenu du document Diffgram.|  
|Validate|Permet de valider le document XML en utilisant un DTD (Document Type Definition) ou un schéma XSD (XML Schema definition).|  
|XPath|Lance les requêtes et les évaluations XPath.|  
|XSLT|Effectue les transformations XSL sur les documents XML.|  
  
### <a name="diff-operation"></a>Opération Diff  
 L'opération Diff peut être configurée pour utiliser un algorithme de comparaison différent selon que la comparaison doive être rapide ou précise. Elle peut également être configurée pour sélectionner automatiquement une comparaison rapide ou précise en fonction de la taille des documents comparés.  
  
 L'opération Diff comprend un ensemble d'options permettant de personnaliser la comparaison XML. Le tableau ci-dessous décrit les options disponibles.  
  
|Option|Description|  
|------------|-----------------|  
|**IgnoreComments**|Valeur indiquant si les nœuds de commentaires sont comparés.|  
|**IgnoreNamespaces**|Valeur indiquant si les URI (Uniform Resource Identifier) d'espace de noms des noms d'un élément et de son attribut sont comparés. Si cette option a pour valeur `true`, deux éléments ayant le même nom local mais un espace de noms différent sont considérés comme identiques.|  
|**IgnorePrefixes**|Valeur indiquant si les préfixes des noms d'élément et d'attribut sont comparés. Si cette option a pour valeur `true,` deux éléments ayant le même nom local mais des URI d'espaces de noms et des préfixes différents sont considérés comme identiques.|  
|**IgnoreXMLDeclaration**|Valeur indiquant si les déclarations XML sont comparées.|  
|**IgnoreOrderOfChildElements**|Valeur indiquant si l'ordre des éléments enfants est comparé. Si cette option a pour valeur `true`, les éléments enfants qui diffèrent uniquement par leur position dans la liste des frères sont considérés comme identiques.|  
|**IgnoreWhiteSpaces**|Valeur indiquant si les espaces blancs sont comparés.|  
|**IgnoreProcessingInstructions**|Valeur indiquant si les instructions de traitement sont comparées.|  
|**IgnoreDTD**|Valeur indiquant si le schéma DTD est ignoré.|  
  
### <a name="merge-operation"></a>Opération de fusion  
 Lorsque vous utilisez une instruction XPath pour identifier l'emplacement de fusion dans le document source, cette instruction est supposée retourner un nœud unique. Si elle retourne plusieurs nœuds, seul le premier est utilisé. Le contenu du deuxième document est fusionné sous le premier nœud que la requête XPath retourne.  
  
### <a name="xpath-operation"></a>Opération XPath  
 L'opération XPath peut être configurée pour utiliser différents types de fonctionnalités XPath.  
  
-   Sélectionnez l’option **Évaluation** pour implémenter des fonctions XPath telles que sum().  
  
-   Sélectionnez l'option **Liste de nœuds** pour renvoyer les nœuds sélectionnés sous forme de fragment XML.  
  
-   Sélectionnez l'option **Valeurs** pour renvoyer les valeurs de texte de tous les nœuds sélectionnés, concaténées en une chaîne.  
  
### <a name="validation-operation"></a>Opération de validation  
 L'opération de validation peut être configurée pour utiliser un schéma DTD (Document Type Definition) ou XSD (XML Schema definition).  
  
 Activez `ValidationDetails` pour obtenir une sortie d’erreur détaillée. Pour plus d’informations, consultez [Validate XML with the XML Task](xml-task.md).  
  
## <a name="xml-document-encoding"></a>Encodage de document XML  
 La tâche XML prend en charge la fusion de documents Unicode uniquement. Cela signifie que la tâche peut appliquer l'opération de fusion uniquement aux documents ayant un encodage Unicode. L'utilisation d'autres encodages provoquera l'échec de la tâche XML.  
  
> [!NOTE]  
>  Les opérations Diff et Patch comprennent une option qui ignore la déclaration XML dans les données XML du deuxième opérande, ce qui permet d'utiliser des documents avec d'autres encodages dans ces opérations.  
  
 Pour vérifier que le document XML peut être utilisé, vérifiez la déclaration XML. Celle-ci doit explicitement indiquer UTF-8, qui représente l'encodage unicode sur 8 bits.  
  
 La balise suivante montre l'encodage Unicode sur 8 bits.  
  
 `<?xml version="1.0" encoding="UTF-8"?>`  
  
## <a name="custom-logging-messages-available-on-the-xml-task"></a>Messages de journalisation personnalisés disponibles dans la tâche XML  
 Le tableau suivant décrit l'entrée de journal personnalisée de la tâche XML. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée de journal|Description|  
|---------------|-----------------|  
|`XMLOperation`|Fournit des informations sur l'opération que la tâche effectue.|  
  
## <a name="configuration-of-the-xml-task"></a>Configuration de la tâche XML  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche XML &#40;page général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Validation XML avec la tâche XML](xml-task.md)  
  
-   [Page expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition des propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-xml-task"></a>Configuration par programme de la tâche XML  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.XMLTask.XMLTask>  
  
## <a name="related-tasks"></a>Tâches associées  
 [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a>Contenu connexe  
  
-   Entrée de Blog, [XML Destination Script Component](http://agilebi.com/jwelch/2007/06/02/xml-destination-script-component/), sur agilebi.com  
  
-   Exemple CodePlex, [Process XML Data Package Sample](https://msftisprodsamples.codeplex.com/wikipage?title=SS2008!Process%20XML%20Data%20Package%20Sample&version=10&ProjectName=msftisprodsamples), sur www.codeplex.com  
  
