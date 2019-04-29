---
title: Exigences de Type défini par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 63f297f1a2a3ae738e00e37acf381b830ced9e7b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919658"
---
# <a name="user-defined-type-requirements"></a>Configuration requise pour les types définis par l'utilisateur
  Vous devez prendre plusieurs décisions de conception importantes lors de la création d’un type défini par l’utilisateur (UDT) doit être installé dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour la plupart des types définis par l'utilisateur, il est recommandé de créer un type défini par l'utilisateur sous forme de structure mais il est également possible de le créer sous forme de classe. La définition de l'UDT doit être conforme aux spécifications de création d'UDT afin de pouvoir l'enregistrer avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="requirements-for-implementing-udts"></a>Configuration requise pour l'implémentation des types définis par l'utilisateur  
 Pour s'exécuter dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], votre UDT doit implémenter les éléments requis suivants dans sa définition :  
  
 L'UDT doit spécifier l'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`. Le recours à l'attribut `System.SerializableAttribute` est facultative mais recommandé.  
  
-   L'UDT doit implémenter l'interface `System.Data.SqlTypes.INullable` dans la classe ou la structure en créant une méthode publique `static` (`Shared` dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic) `Null`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est par défaut compatible avec la valeur NULL. Ceci est nécessaire pour que le code exécuté dans l'UDT puisse être en mesure de reconnaître une valeur NULL.  
  
-   L'UDT doit contenir une méthode publique `static` (ou `Shared`) `Parse` qui prend en charge l'analyse, ainsi qu'une méthode publique `ToString` pour convertir l'objet en une représentation sous forme de chaîne.  
  
-   Un UDT doté d'un format de sérialisation défini par l'utilisateur doit implémenter l'interface `System.Data.IBinarySerialize` et fournir une méthode `Read` et une méthode `Write`.  
  
-   L'UDT doit implémenter `System.Xml.Serialization.IXmlSerializable` ou tous les champs et les propriétés publics doivent être de types qui autorisent la sérialisation XML ou munis de l'attribut `XmlIgnore` si une substitution de la sérialisation standard est requise.  
  
-   Chaque objet UDT doit être soumis à une seule sérialisation. La validation échoue si les routines de sérialisation ou désérialisation reconnaissent plusieurs représentations d'un objet en particulier.  
  
-   `SqlUserDefinedTypeAttribute.IsByteOrdered` doit avoir la valeur `true` pour comparer des données dans la marque d'ordre d'octets. Si l'interface IComparable n'est pas implémentée et que `SqlUserDefinedTypeAttribute.IsByteOrdered` a la valeur `false`, les comparaisons de marque d'ordre d'octets échoueront.  
  
-   Un UDT défini dans une classe doit disposer d'un constructeur public qui n'accepte aucun argument. Vous pouvez éventuellement créer des constructeurs de classe surchargés supplémentaires.  
  
-   L'UDT doit dévoiler les éléments de données sous forme de champs publics ou de procédures de propriété.  
  
-   Noms publics ne peuvent pas comporter plus de 128 caractères et doit être conforme à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] règles de nommage pour les identificateurs tel que défini dans [identificateurs de base de données](../databases/database-identifiers.md).  
  
-   Les colonnes `sql_variant` ne peuvent pas contenir les instances d'un UDT.  
  
-   Les membres hérités ne sont pas accessibles depuis [!INCLUDE[tsql](../../includes/tsql-md.md)] puisque le système de type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas compatible avec la hiérarchie d'héritage entre UDT. Toutefois, vous pouvez recourir à la fonction d'héritage au moment de structurer vos classes et pouvez appeler ces méthodes dans l'implémentation du code managé du type.  
  
-   Hormis le constructeur de classe, les membres ne peuvent pas être surchargés. Si vous créez une méthode surchargée, aucune erreur ne se produit au moment d'inscrire l'assembly ou de créer le type dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La détection de la méthode surchargée a lieu au moment de l'exécution et non lors de la création du type. Les méthodes surchargées peuvent exister dans la classe tant qu'elles ne sont jamais appelées. Une erreur est générée dès que vous appelez la méthode surchargée.  
  
-   Tous les membres `static` (ou `Shared`) doivent être déclarés en tant que constantes ou en lecture seule. Les membres statiques ne peuvent pas être mutables.  
  
-   Si le champ `SqlUserDefinedTypeAttribute.MaxByteSize` est défini sur -1, l'UDT sérialisé peut être aussi volumineux que la taille limite de l'objet LOB (actuellement 2 Go). La taille de l'UDT ne peut pas dépasser la valeur spécifiée dans le champ `MaxByteSized`.  
  
> [!NOTE]  
>  Bien qu'elle ne soit pas utilisée par le serveur pour effectuer des comparaisons, vous pouvez implémenter l'interface `System.IComparable` si vous le souhaitez. Cette interface propose une seule et unique méthode, `CompareTo`. Elle intervient côté client dans des situations où il est préférable de comparer ou de classer avec précision des valeurs de type défini par l'utilisateur (UDT).  
  
## <a name="native-serialization"></a>Sérialisation native  
 Le choix du bon attribut de sérialisation pour votre UDT dépend du type d'UDT que vous essayez de créer. Le format de sérialisation `Native` utilise une structure très simple qui permet à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de stocker une représentation native efficace du type défini par l'utilisateur sur le disque. Le format `Native` est recommandé si l'UDT est simple et contient uniquement des champs des types suivants :  
  
 **bool**, **byte**, **sbyte**, **short**, **ushort**, **int**, **uint**, **long**, **ulong**, **float**, **double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 Les types valeur sont composés de champs des types ci-dessus sont de bons candidats pour `Native` mettre en forme, telles que `structs` en Visual c# (ou `Structures` qu’elles sont connues en Visual Basic). Par exemple, un UDT spécifié avec le format de sérialisation `Native` peut contenir un champ d'un autre UDT également spécifié avec le format `Native`. Si la définition de l'UDT est plus complexe et contient des types de données non inscrits dans la liste ci-dessus, vous devez spécifier à la place le format de sérialisation `UserDefined`.  
  
 Le format `Native` pose les conditions suivantes :  
  
-   Le type ne doit spécifier aucune valeur pour `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize`.  
  
-   Tous les champs doivent être sérialisables.  
  
-   L'attribut `System.Runtime.InteropServices.StructLayoutAttribute` doit être spécifié en tant que `StructLayout.LayoutKindSequential` si le type défini par l'utilisateur (UDT) est défini dans une classe et non une structure. Cet attribut contrôle la disposition physique des champs de données et est utilisé pour contraindre les membres à se placer dans l'ordre dans lequel ils apparaissent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise cet attribut pour déterminer l'ordre des champs des UDT au moyen de plusieurs valeurs.  
  
 Pour obtenir un exemple d’UDT défini avec `Native` sérialisation, consultez l’UDT Point dans [Coding User-Defined Types](creating-user-defined-types-coding.md).  
  
## <a name="userdefined-serialization"></a>Sérialisation UserDefined  
 Le paramètre de mise en forme `UserDefined` de l'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` permet au développeur de maîtriser entièrement le format binaire. Lorsque vous spécifiez la propriété d'attribut `Format` en tant que `UserDefined`, vous devez effectuer les opérations suivantes dans votre code :  
  
-   Spécifiez la propriété d'attribut `IsByteOrdered` facultative. La valeur par défaut est `false`.  
  
-   Spécifiez la propriété `MaxByteSize` de `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.  
  
-   Écrivez du code pour implémenter les méthodes `Read` et `Write` pour l'UDT en implémentant l'interface `System.Data.Sql.IBinarySerialize`.  
  
 Pour obtenir un exemple d’UDT défini avec `UserDefined` sérialisation, consultez l’UDT Currency dans [Coding User-Defined Types](creating-user-defined-types-coding.md).  
  
> [!NOTE]  
>  Les champs UDT doivent utiliser la sérialisation native ou être persistants pour pouvoir être indexés.  
  
## <a name="serialization-attributes"></a>Attributs de sérialisation  
 Les attributs déterminent la façon dont la sérialisation est utilisée pour construire la représentation de stockage des types définis par l'utilisateur et pour transmettre des types définis par l'utilisateur par valeur au client. Vous devez spécifier l'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` au moment de créer l'UDT. L'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` indique que la classe est un UDT et précise le stockage de cet UDT. Bien que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne l'exige pas, si vous le souhaitez, vous pouvez spécifier l'attribut `Serializable`.  
  
 L'attribut `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` présente les propriétés suivantes :  
  
 `Format`  
 Spécifie le format de sérialisation qui peut être `Native` ou `UserDefined` en fonction des types de données de l'UDT.  
  
 `IsByteOrdered`  
 Valeur `Boolean` qui détermine comment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des comparaisons binaires sur le type défini par l'utilisateur.  
  
 `IsFixedLength`  
 Indique si toutes les instances de cet UDT ont la même longueur.  
  
 `MaxByteSize`  
 Taille maximale de l'instance, en octets. Vous devez spécifier `MaxByteSize` avec le format de sérialisation `UserDefined`. Pour un type défini par l'utilisateur assorti d'une sérialisation définie par l'utilisateur, `MaxByteSize` fait référence à la taille totale du type défini par l'utilisateur dans sa forme sérialisée, telle que définie par l'utilisateur. La valeur de `MaxByteSize` doit figurer dans une plage de 1 à 8 000 ou être définie sur -1 pour indiquer que la taille de l'UDT est supérieure à 8 000 octets (la taille totale ne peut pas dépasser la taille d'objet LOB maximale). Imaginez un type défini par l'utilisateur assorti d'une propriété d'une chaîne de 10 caractères (`System.Char`). Lorsque l’UDT est sérialisé à l’aide de BinaryWriter, la taille totale de la chaîne sérialisée est de 22 octets : 2 octets par caractère Unicode UTF-16, multiplié par le nombre maximal de caractères de plus de contrôle 2 octets de surcharge induite par la sérialisation d’un flux binaire. Ainsi, pour déterminer la valeur de `MaxByteSize`, il convient de prendre en compte la taille totale du type défini par l'utilisateur (UDT) sérialisé : la taille des données sérialisées sous forme binaire, plus la charge mémoire générée par la sérialisation.  
  
 `ValidationMethodName`  
 Nom de la méthode utilisée pour valider des instances du type défini par l'utilisateur.  
  
### <a name="setting-isbyteordered"></a>Définition de la propriété IsByteOrdered  
 En attribuant la valeur `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered` à la propriété `true`, vous garantissez que les données binaires sérialisées peuvent être utilisées pour un classement sémantique des informations. Par conséquent, chaque instance d'un objet UDT ordonné par octet peut avoir une seule représentation sérialisée. Lorsque vous soumettez les octets sérialisés à une comparaison dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les résultats doivent être les mêmes que si vous réalisiez cette opération de comparaison dans le code managé. Les fonctionnalités suivantes sont également prises en charge lorsque `IsByteOrdered` a la valeur `true` :  
  
-   Possibilité de créer des index dans les colonnes de ce type.  
  
-   Possibilité de créer des clés primaires et étrangères ainsi que des contraintes CHECK et UNIQUE dans les colonnes de ce type.  
  
-   Possibilité d'utiliser les clauses ORDER BY, GROUP BY et PARTITION BY de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Dans ces cas, la représentation binaire du type est utilisée pour déterminer l'ordre.  
  
-   Possibilité d'utiliser des opérateurs de comparaison dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Possibilité de rendre persistantes des colonnes calculées de ce type.  
  
 Notez que les formats de sérialisation `Native` et `UserDefined` prennent tous les deux en charge les opérateurs de comparaison suivants lorsque `IsByteOrdered` a la valeur `true` :  
  
-   Égal à (=)  
  
-   Différent de (!=)  
  
-   Supérieur à (>)  
  
-   Inférieur à (\<)  
  
-   Supérieur ou égal à (> =)  
  
-   Inférieur ou égal à (< =)  
  
### <a name="implementing-nullability"></a>Implémentation de la possibilité de valeur NULL  
 En plus de spécifier correctement les attributs de vos assemblys, votre classe doit également prendre en charge la possibilité de valeur NULL. Les types définis par l'utilisateur (UDT) chargés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont compatibles avec la valeur NULL mais, pour que l'UDT puisse reconnaître une valeur NULL, la classe doit implémenter l'interface `INullable`. Pour plus d’informations et un exemple montrant comment implémenter la possibilité de valeur NULL dans un UDT, consultez [Coding User-Defined Types](creating-user-defined-types-coding.md).  
  
### <a name="string-conversions"></a>Conversions de chaînes  
 Pour prendre en charge la conversion de chaînes vers et depuis l'UDT, vous devez préciser une méthode `Parse` et une méthode `ToString` dans votre classe. La méthode `Parse` permet de convertir une chaîne en un type défini par l'utilisateur. Elle doit être déclarée comme `static` (ou `Shared` dans Visual Basic) et accepter un paramètre de type `System.Data.SqlTypes.SqlString`. Pour plus d’informations et un exemple montrant comment implémenter le `Parse` et `ToString` méthodes, consultez [Coding User-Defined Types](creating-user-defined-types-coding.md).  
  
## <a name="xml-serialization"></a>Sérialisation XML  
 Les UDT doivent prendre en charge la conversion vers et depuis le type de données `xml` en tenant compte des exigences de la sérialisation XML. L'espace de noms `System.Xml.Serialization` contient des classes servant à sérialiser des objets en documents au format XML ou en flux. Vous pouvez choisir d'implémenter la sérialisation `xml` par le biais de l'interface `IXmlSerializable` qui offre un format personnalisé pour la sérialisation et la désérialisation XML.  
  
 Outre les conversions explicites entre les UDT et `xml`, la sérialisation XML vous offre les possibilités suivantes :  
  
-   Utiliser `Xquery` sur les valeurs d'instances d'UDT après conversion en type de données `xml`.  
  
-   Utiliser des UDT dans des requêtes paramétrables et des méthodes Web à l'aide des services Web XML natifs dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Utiliser des UDT pour recevoir un chargement en masse de données XML.  
  
-   Sérialiser des datasets contenant des tables avec des colonnes UDT.  
  
 Les UDT ne sont pas sérialisés dans les requêtes FOR XML. Pour exécuter une requête FOR XML qui affiche la sérialisation XML des UDT, convertissez explicitement chaque colonne UDT en type de données `xml` dans l'instruction SELECT. Vous pouvez aussi convertir explicitement les colonnes en types `varbinary`, `varchar` ou `nvarchar`.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un type défini par l’utilisateur](creating-user-defined-types.md)  
  
  
