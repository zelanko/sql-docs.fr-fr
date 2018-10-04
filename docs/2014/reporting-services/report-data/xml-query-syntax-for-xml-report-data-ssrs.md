---
title: Syntaxe de requête XML pour les données de rapport XML (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 65eed443f671f18944ce381a011498e3ca23af4e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102889"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a>Syntaxe de requête XML pour les données de rapport XML (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]vous permet de créer des datasets pour des sources de données XML. Après avoir défini une source de données, vous devez créer une requête pour le dataset. Selon le type de données XML vers lequel pointés la source de données, vous créez la requête de dataset en incluant un XML `Query` ou un chemin d’accès de l’élément. Un document XML `Query` commence par un  **\<requête >** balise et inclut des espaces de noms et les éléments XML qui varient en fonction de la source de données. Un chemin d'accès à un élément opère indépendamment des espaces de noms ; il précise les nœuds et les attributs de nœud à utiliser à partir des données XML sous-jacentes avec une syntaxe similaire à la syntaxe XPath. Pour plus d’informations sur les chemins d’éléments, consultez [Syntaxe du chemin vers l’élément pour des données de rapport XML &#40;SSRS&#41;](report-data-ssrs.md).  
  
 Vous pouvez créer une source de données XML pour les types de données XML suivants :  
  
-   Documents XML désignés par une URL utilisant le protocole HTTP  
  
-   Points de terminaison du service Web retournant des données XML  
  
-   Données XML incorporées  
  
 La manière dont vous spécifiez une `Query` XML ou un chemin d'accès à un élément dépend du type de données XML.  
  
 Pour un document XML, le code XML `Query` est facultatif. Si elle est incluse, elle peut contenir un `ElementPath` XML facultatif. La valeur de l'élément `ElementPath` XML utilise la syntaxe du chemin d'accès à l'élément. Vous devez inclure les `Query` et XML `ElementPath` pour traiter correctement les espaces de noms lorsqu’il est nécessaire par les données XML à partir de la source de données.  
  
 Dans le cadre d'un point de terminaison de service Web désigné par l'URL d'une chaîne de connexion, `Query` XML définit soit la méthode du service Web, soit l'action SOAP, soit les deux. Le fournisseur de données XML crée une demande de service Web qui extrait les données XML à utiliser pour le rapport.  
  
> [!NOTE]  
>  Lorsque l'espace de noms d'un service Web comporte une barre oblique (`/)`, incluez à la fois la méthode du service Web et l'action SOAP de sorte que l'extension de traitement des données XML puisse correctement extraire l'espace de noms.  
  
 Pour un document XML incorporé, le code XML `Query` définit les données XML incorporées à utiliser, inclut des espaces de noms facultatifs et contient un XML facultatif `ElementPath`...  
  
## <a name="specifying-query-parameters-for-xml-data"></a>Spécification de paramètres de la requête pour des données XML  
 Vous pouvez spécifier des paramètres de la requête pour les documents XML.  
  
-   Pour les requêtes URL, les paramètres de la requête sont inclus en tant que paramètres URL standard.  
  
-   Pour les requêtes du service Web, les paramètres de la requête sont passés à la méthode du service Web. Pour définir un paramètre de requête, utilisez la page **Paramètres** de la boîte de dialogue **Propriétés du dataset** . Pour plus d’informations, consultez [boîte de dialogue Propriétés de Dataset, paramètres](dataset-properties-dialog-box-parameters.md).  
  
### <a name="example"></a>Exemple  
 Les exemples fournis dans le tableau ci-dessous illustrent la manière d'extraire des données du service Web Report Server, un document XML et des données XML incorporées.  
  
|Source de données XML|Exemple de requête|  
|---------------------|-------------------|  
|Données XML du service Web à partir de la méthode de ListChildren.|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="http://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|Données XML du service Web issues de SoapAction.|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|Document XML ou données XML incorporées qui utilisent des espaces de noms.<br /><br /> Élément de requête spécifiant des espaces de noms pour un chemin d'accès à un élément.|`<Query xmlns:es="http://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|Document XML incorporé.|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|Document XML qui utilise la valeur par défaut.|*Aucune requête*.<br /><br /> Le chemin d'accès à l'élément provient du document XML lui-même et est indépendant des espaces de noms.|  
  
> [!NOTE]  
>  Le premier exemple de service web répertorie le contenu du serveur de rapports qui utilise la méthode <xref:ReportService2006.ReportingService2006.ListChildren%2A> . Pour exécuter cette requête, vous devez créer une nouvelle source de données et définir la chaîne de connexion sur http://localhost/reportserver/reportservice2006.asmx. Le <xref:ReportService2006.ReportingService2006.ListChildren%2A> méthode accepte deux paramètres : `Item` et `Recursive`. Définir la valeur par défaut `Item` à `/` et `Recursive` à `1`.  
  
## <a name="specifying-namespaces"></a>Définition d'espaces de noms  
 Utilisez le code XML `Query` élément pour spécifier les espaces de noms qui sont utilisés dans les données XML à partir de la source de données. La requête XML suivante utilise l'espace de noms `sales`. Les nœuds `ElementPath` XML de `sales:LineItems` et `sales:LineItem` utilisent l'espace de noms `sales`.  
  
```  
<Query xmlns:sales=  
"http://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      http://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 Pour spécifier l’espace de noms de fournisseur de données afin que l’espace de noms par défaut reste vide, utilisez `xmldp`. Cela est illustré par l'exemple suivant.  
  
### <a name="example"></a>Exemple  
 Les exemples suivants utilisent le document XML DPNamespace.xml fourni à titre d'illustration à la suite du tableau ci-après. Ce tableau présente deux exemples de syntaxe ElementPath XML incluant des préfixes d'espaces de noms.  
  
|Élément de requête XML|Champs obtenus dans le dataset|  
|-----------------------|-------------------------------------|  
|\<Query/>|R : la valeur http://schemas.microsoft.com/...<br /><br /> Valeur b : http://schemas.microsoft.com/...<br /><br /> Valeur C: http://schemas.microsoft.com/...|  
|\<xmldp:Query xmlns:xmldp = « http://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery« xmlns:ns = « http://schemas.microsoft.com/... » ><br /><br /> \<xmldp:ElementPath > racine {}/ns:Element2 / nœud\</xmldp:ElementPath ><br /><br /> \</xmldp:Query >|Valeur D<br /><br /> Valeur E<br /><br /> Valeur F|  
  
#### <a name="xml-document-dpnamespacexml"></a>Document XML : DPNamespace.xml  
 Vous pouvez copier ce document XML et l'enregistrer dans une URL disponible pour être utilisée en tant que source de données par le Concepteur de rapports : par exemple http://localhost/DPNamespace.xml.  
  
```  
<Root xmlns:ns="http://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Type de connexion XML &#40;SSRS&#41;](xml-connection-type-ssrs.md)   
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
