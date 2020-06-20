---
title: Spécifications et limitations relatives aux collections de schémas XML sur le serveur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- identifiers [XML schema collections]
- XML schema collections [SQL Server], limitations
- substitution groups [XML in SQL Server]
- XML schema collections [SQL Server], guidelines
- lax validation
- enumeration facets [XML in SQL Server]
- decimal precision [XML in SQL Server]
- repeated XML schema collection values
- schema collections [SQL Server], limitations
- time zones [XML in SQL Server]
- precision decimals [XML in SQL Server]
- schema collections [SQL Server], guidelines
- lexical representation
ms.assetid: c2314fd5-4c6d-40cb-a128-07e532b40946
author: rothja
ms.author: jroth
ms.openlocfilehash: 41e27204bf472d905f420d665c206b840582e8de
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065488"
---
# <a name="requirements-and-limitations-for-xml-schema-collections-on-the-server"></a>Spécifications et limitations relatives aux collections de schémas XML sur le serveur
  La validation XSD (XML Schema Definition Language) des colonnes SQL utilisant le type de données `xml` fait l'objet de certaines limitations, lesquelles sont exposées dans le tableau suivant. Les recommandations à suivre pour modifier un schéma XSD afin qu'il soit compatible avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]y sont abordées. Les rubriques de cette section fournissent des informations supplémentaires concernant les limitations spécifiques, ainsi qu'une assistance pour leur utilisation.  
  
|Élément|Limitation|  
|----------|----------------|  
|**minOccurs** et **maxOccurs**|Les valeurs des attributs **minOccurs** et **maxOccurs** doivent tenir dans des entiers à 4 octets. Les schémas non conformes sont rejetés par le serveur.|  
|**\<xsd:choice>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]rejette les schémas qui ont une **\<xsd:choice>** particule sans enfants, sauf si la particule est définie avec une valeur d’attribut **minOccurs** égale à zéro.|  
|**\<xsd:include>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend actuellement pas en charge cet élément. Les schémas XML incluant cet élément seront rejetés par le serveur.<br /><br /> En guise de solution, les schémas XML qui incluent la **\<xsd:include>** directive peuvent être prétraités pour copier et fusionner le contenu de tous les schémas inclus dans un seul schéma à charger sur le serveur. Pour plus d’informations, consultez [Prétraiter un schéma pour fusionner des schémas inclus](preprocess-a-schema-to-merge-included-schemas.md).|  
|**\<xsd:key>**, **\<xsd:keyref>** et**\<xsd:unique>**|Actuellement, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge ces contraintes basées sur XSD pour appliquer l'unicité ou établir des clés ou des références de clés. Les schémas XML contenant ces éléments ne peuvent pas être inscrits.|  
|**\<xsd:redefine>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend actuellement pas en charge cet élément. Pour obtenir des informations sur une autre façon de mettre à jour des schémas, consultez [Élément &#60;xsd:redefine&#62;](the-xsd-redefine-element.md)y sont abordées.|  
|**\<xsd:simpleType>** valeurs|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend uniquement en charge la précision à la milliseconde pour les types simples comportant un composant seconde autre que `xs:time` et `xs:dateTime`, et une précision de 100 nanosecondes pour `xs:time` et `xs:dateTime`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impose des limites à toutes les énumérations de types simples XSD reconnus.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne prend pas en charge l’utilisation de la valeur « NaN » dans les **\<xsd:simpleType>** déclarations.<br /><br /> Pour plus d’informations, consultez[Valeurs pour les déclarations &#60;xsd:simpleType&#62;](values-for-xsd-simpletype-declarations.md)y sont abordées.|  
|**xsi:schemaLocation** et **xsi:noNamespaceSchemaLocation**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ignore ces attributs s'ils sont présents dans les données d'instance XML insérées dans une colonne ou une variable de type de données `xml`.|  
|**XS : QName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne prend pas en charge les types dérivés de **XS : QName** qui utilisent un élément de restriction de schéma XML.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne prend pas en charge les types Union avec **XS : QName** en tant qu’élément membre.<br /><br /> Pour plus d’informations, consultez [The xs:QName Type](the-xs-qname-type.md).|  
|Ajout de membres à un groupe de substitution existant|Vous ne pouvez pas ajouter des membres à un groupe de substitution existant dans une collection de schémas XML. Un groupe de substitution dans un schéma XML est restreint en cela que l’élément de tête et tous les éléments membres doivent être définis dans la même instruction {CREATE &#124; ALTER} XML SCHEMA COLLECTION.|  
|Formes canoniques et restrictions de modèle|La représentation canonique d'une valeur ne peut enfreindre la restriction de modèle pour son type. Pour plus d’informations, consultez [Canonical Forms and Pattern Restrictions](canonical-forms-and-pattern-restrictions.md).|  
|Facettes d'énumération|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les schémas XML avec des types présentant des facettes de modèles ou des énumérations enfreignant ces facettes.|  
|Longueur de facette|Les facettes **Length**, **minLength**et **MaxLength** sont stockées en tant que `long` type. type codé sur 32 bits. Par conséquent, la plage de valeurs acceptables pour ces valeurs est 2 <sup>^</sup> 31.|  
|Attribut d'ID|Chaque composant de schéma XML peut avoir un attribut d'ID. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]applique l’unicité des **\<xsd:attribute>** déclarations de type **ID** , mais ne stocke pas ces valeurs. L’étendue pour l’application de l’unicité est l’instruction {CREATE &#124; ALTER} XML SCHEMA COLLECTION.|  
|Type ID|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne prend pas en charge les éléments de type **XS : ID**, **XS : IDREF**ou **XS : IDREFS**. Un schéma peut ne pas déclarer les éléments de ce type, ou les éléments dérivés par restriction ou par extension de ce type.|  
|Espace de noms local|L’espace de noms local doit être spécifié explicitement pour l' **\<xsd:any>** élément. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette les schémas qui utilisent une chaîne vide ("") comme valeur de l’attribut d’espace de noms. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite en lieu et place l'utilisation explicite de « ##local » pour indiquer qu'un élément ou un attribut non qualifié sera utilisé en tant qu'instance du caractère générique.|  
|Type mixte et contenu simple|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge la restriction d'un type mixte à du contenu simple. Pour plus d’informations, consultez [Mixed Type and Simple Content](mixed-type-and-simple-content.md).|  
|Type NOTATION|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'accepte pas les valeurs de type NOTATION.|  
|Conditions de mémoire insuffisante|La manipulation de collections de schémas XML volumineuses peut entraîner des conditions de mémoire insuffisante. Pour trouver des solutions à ces problèmes, consultez [Collections de schémas XML volumineuses et conditions de mémoire insuffisante](large-xml-schema-collections-and-out-of-memory-conditions.md).|  
|Valeurs répétées|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette les schémas où l'attribut block ou final comporte des valeurs répétées comme « restriction restriction » et « extension extension ».|  
|Identificateurs de composant de schéma|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] limite les identificateurs de composant de schéma à une longueur maximale de 1 000 caractères Unicode. De plus, l'emploi de paires de caractères de substitution au sein des identificateurs n'est pas pris en charge.|  
|Informations de fuseau horaire|Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, les informations de fuseau horaire sont totalement prises en charge pour les valeurs `xs:date`, `xs:time` et `xs:dateTime` pour la validation de schéma XML. Avec le mode de compatibilité descendante de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , les informations de fuseau horaire sont toujours normalisées en Temps universel coordonné (heure de Greenwich). Pour les éléments de type `dateTime`, le serveur convertit l'heure fournie à l'heure GMT en se basant sur la valeur de décalage horaire (« -05:00 ») et en retournant l'heure GMT correspondante.|  
|Types union|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les restrictions des types union.|  
|Décimales de précision de variable|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les décimales de précision de variable. Le type **xs:decimal** représente des nombres de décimales de précision arbitraire. Les processeurs XML conformes minimaux doivent prendre en charge les nombres décimaux avec un minimum de `totalDigits=18`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge `totalDigits=38,` , mais limite les chiffres fractionnels à 10. Toutes les valeurs instanciées de **xs:decimal** sont représentées en interne par le serveur en utilisant le type numeric SQL (38, 10).|  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Formes canoniques et restrictions de modèle](canonical-forms-and-pattern-restrictions.md)|Explique les formes canoniques et restrictions de modèle.|  
|[Composants génériques et validation de contenu](wildcard-components-and-content-validation.md)|Décrit les limitations liées à l'utilisation des caractères génériques, de la validation de type lax et des éléments anyType avec des collections de schémas XML.|  
|[Élément &#60;xsd:redefine&#62;](the-xsd-redefine-element.md)|Explique la limitation de l’utilisation de l' \<xsd:redefine> élément et décrit une solution de contournement.|  
|[The xs:QName Type](the-xs-qname-type.md)|Décrit la limitation relative au type xs:QName.|  
|[Valeurs pour les déclarations &#60;xsd:simpleType&#62;](values-for-xsd-simpletype-declarations.md)|Décrit les restrictions appliquées aux \<xsd:simpleType> déclarations.|  
|[facettes d'énumération](enumeration-facets.md)|Décrit la limitation relative aux facettes d'énumération.|  
|[Type mixte et contenu simple](mixed-type-and-simple-content.md)|Décrit la limitation relative à la restriction d'un type mixte à un contenu simple.|  
|[Collections de schémas XML volumineuses et conditions de mémoire insuffisante](large-xml-schema-collections-and-out-of-memory-conditions.md)|Fournit des solutions pour la condition de mémoire insuffisante qui se produit parfois avec les grandes collections de schémas.|  
|[Modèles de contenu non déterministes](non-deterministic-content-models.md)|Décrit les limitations relatives aux modèles de contenu non déterministes.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server de &#40;de données XML&#41;](xml-data-sql-server.md)   
 [Comparer du XML typé et du XML non typé](compare-typed-xml-to-untyped-xml.md)   
 [Accorder des autorisations sur une collection de schémas XML](grant-permissions-on-an-xml-schema-collection.md)   
 [Contrainte d’attribution de particule unique](unique-particle-attribution-constraint.md)   
 [Collections de schémas XML &#40;SQL Server&#41;](xml-schema-collections-sql-server.md)  
  
  
